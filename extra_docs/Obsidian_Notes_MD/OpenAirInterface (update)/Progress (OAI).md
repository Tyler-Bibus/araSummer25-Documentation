
### UE Patch:
- Applied all patches
- TODO: Build & Test
---
%% This will be the one that will be fairly difficult to apply...  %%
### gNB Patch:
-  gNB_scheduler_RA.c is different enough from old version, will take more effort.
- TODO: Apply patch completely
> Not Applied
>> gNB_scheduler_RA.c
>> nr_rrc_config.c; Diff 3
>> ~~usrp_lib.cpp~~
>> ~~gnb.sa.band78.fr1.106PRB.usrpb210.conf~~

**gNB_scheduler_RA.c**
- I believe that diff 1 is maybe not needed, as they do not every refer to a final/last dl slot... (unless the last_slot stuff was added)
Note location of diff 1 is most likely located, just not implemented yet...

*gNB_scheduler_RA.c applied patches: (1)*
``` diff
@@ -703,7 +704,8 @@ void nr_generate_Msg3_retransmission(module_id_t module_idP, int CC_id, frame_t
   int mu = ul_bwp->scs;
   uint8_t K2 = *pusch_TimeDomainAllocationList->list.array[ra->Msg3_tda_id]->k2;
   const int sched_frame = frame + (slot + K2 >= nr_slots_per_frame[mu]);
-  const int sched_slot = (slot + K2) % nr_slots_per_frame[mu];
+  //const int sched_slot = (slot + K2) % nr_slots_per_frame[mu];
+  const int sched_slot = 18 % nr_slots_per_frame[mu]; //Joshua
 
   if (is_xlsch_in_slot(RC.nrmac[module_idP]->ulsch_slot_bitmap[sched_slot / 64], sched_slot)) {
     // beam association for FR2
```

gnB_scheduler_RA.c diff 3 has **NOT** been applied yet:
``` diff
@@ -893,13 +895,16 @@ void nr_get_Msg3alloc(module_id_t module_id,
   const int n_slots_frame = nr_slots_per_frame[mu];
   uint8_t k2 = 0;
   if (frame_type == TDD) {
-    int msg3_slot = get_first_ul_slot(tdd->nrofDownlinkSlots, tdd->nrofDownlinkSymbols, tdd->nrofUplinkSymbols);
+    //int msg3_slot = get_first_ul_slot(tdd->nrofDownlinkSlots, tdd->nrofDownlinkSymbols, tdd->nrofUplinkSymbols);
+    int msg3_slot = 8; // Joshua hardcoded the first UL slot index in DDDDDDDSUU
     if (tdd->nrofUplinkSymbols != 0) {
       if (tdd->nrofUplinkSymbols < 3)
         msg3_slot++; // we can't trasmit msg3 in mixed slot if there are less than 3 symbols
       else {
-        Msg3maxsymb = tdd->nrofUplinkSymbols;
-        Msg3start = 14 - tdd->nrofUplinkSymbols;
+        //Msg3maxsymb = tdd->nrofUplinkSymbols;
+        //Msg3start = 14 - tdd->nrofUplinkSymbols;
+        Msg3maxsymb = 14;
+        Msg3start = 0;
       }
     }
     const int nb_periods_per_frame = get_nb_periods_per_frame(tdd->dl_UL_TransmissionPeriodicity);
```

**nr_rrc_config.c; diff 3**
- I believe I have found the correct part. need to just modify and ensure I insert it properly. 
- diff 1 is just a comment, diff 2 is applied.

diff 3:
``` diff
@@ -753,6 +772,37 @@ void nr_rrc_config_ul_tda(NR_ServingCellConfigCommon_t *scc, int min_fb_delay){

else

pusch_timedomainresourceallocation_msg3->startSymbolAndLength = get_SLIV(14 - ul_symb, ul_symb - 1); // starting in fist ul symbol til the last but one

asn1cSeqAdd(&scc->uplinkConfigCommon->initialUplinkBWP->pusch_ConfigCommon->choice.setup->pusch_TimeDomainAllocationList->list,pusch_timedomainresourceallocation_msg3);

+ // New UL TDA index: Msg3 scheduled in the first UL slot in every TDD period - Joshua
+ int dl_slots = 7; // Number of DL slots (DDDDDDD)
+ int s_slot = 1; // One special slot (S)
+ int ul_slots = 2; // Number of UL slots (UU)
+ int total_slots = dl_slots + s_slot + ul_slots;
+ int start_symb = 0;
+ int length_symb = 0;

+ struct NR_PUSCH_TimeDomainResourceAllocation *pusch_timedomainresourceallocation_msg3_first_ul = CALLOC(1, sizeof(struct NR_PUSCH_TimeDomainResourceAllocation));

+ pusch_timedomainresourceallocation_msg3_first_ul->k2 = CALLOC(1, sizeof(long));

+ *pusch_timedomainresourceallocation_msg3_first_ul->k2 = total_slots - 1; // since Msg3 is scheduled in the first UL slot

+ AssertFatal(*pusch_timedomainresourceallocation_msg3_first_ul->k2 < 33, "Computed k2 for msg3 in first UL slot %ld is larger than the range allowed by RRC (0..32)\n", *pusch_timedomainresourceallocation_msg3_first_ul->k2);

+ pusch_timedomainresourceallocation_msg3_first_ul->mappingType = NR_PUSCH_TimeDomainResourceAllocation__mappingType_typeB;

+ pusch_timedomainresourceallocation_msg3_first_ul->startSymbolAndLength = get_SLIV(start_symb, length_symb); // assuming the full UL slot allocation

+ asn1cSeqAdd(&scc->uplinkConfigCommon->initialUplinkBWP->pusch_ConfigCommon->choice.setup->pusch_TimeDomainAllocationList->list, pusch_timedomainresourceallocation_msg3_first_ul);

}

}
```

**usrp_lib.cpp**
 - Application Completed

**gnb.sa.band78.fr1.106PRB.usrpb210.conf**
- Application Completed
---

### Manual GPIO Patch:
- ~~Todo: confirm neeeded...~~
- ~~If needed then we shall apply.~~
-  *this is different, but I based off generated diff in docker image, these changes are not needed anymore.*