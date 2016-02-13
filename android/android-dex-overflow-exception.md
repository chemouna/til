
### Android's DexIndexOverflowException

Whenever you see a build error like :
UNEXPECTED TOP-LEVEL EXCEPTION:
com.android.dex.DexIndexOverflowException: method ID not in [0, 0xffff]: 65536
        at com.android.dx.merge.DexMerger$6.updateIndex(DexMerger.java:484)
        at com.android.dx.merge.DexMerger$IdMerger.mergeSorted(DexMerger.java:261)
        at com.android.dx.merge.DexMerger.mergeMethodIds(DexMerger.java:473)
        at com.android.dx.merge.DexMerger.mergeDexes(DexMerger.java:161)
        at com.android.dx.merge.DexMerger.merge(DexMerger.java:188)
        at com.android.dx.command.dexer.Main.mergeLibraryDexBuffers(Main.java:504)
        at com.android.dx.command.dexer.Main.runMonoDex(Main.java:334)
        at com.android.dx.command.dexer.Main.run(Main.java:277)
        at com.android.dx.command.dexer.Main.main(Main.java:245)
        at com.android.dx.command.Main.main(Main.java:106)

It means you've reached the dreaded 65k methods limit, read
[this documentation](http://developer.android.com/tools/building/multidex.html)
 and apply the solution there
