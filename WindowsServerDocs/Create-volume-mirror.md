---
title: Create volume mirror
ms.custom: na
ms.prod: windows-server-2012
ms.reviewer: na
ms.suite: na
ms.technology: 
  - techgroup-storage
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 48776917-783a-47ff-8da4-1cab77cea34b
---
# Create volume mirror
Creates a volume mirror by using the two specified dynamic disks.

> [!NOTE]
> This command is only available in Windows 7 and Windows Server 2008 R2.

For examples of how this command can be used, see [Examples](#BKMK_examples).

## Syntax

```
create volume mirror [size=<n>] disk=<n>,<n>[,<n>,...] [align=<n>] [noerr] [noerr]
```

## Parameters

|Parameter|Description|
|-------------|---------------|
|size\=<n>|Specifies the amount of disk space, in megabytes \(MB\), that the volume will occupy on each disk. If no size is given, the new volume takes up the remaining free space on the smallest disk and an equal amount of space on each subsequent disk.|
|disk\=<n>,<n>\[,<n>,...\]|Specifies the dynamic disks on which the mirror volume is created. You need two dynamic disks to create a mirror volume. An amount of space that is equal to the size specified with the **size** parameter is allocated on each disk.|
|align\=<n>|Aligns all volume extents to the closest alignment boundary. This parameter is typically used with hardware RAID logical unit number \(LUN\) arrays to improve performance. *n* is the number of kilobytes \(KB\) from the beginning of the disk to the closest alignment boundary.|
|noerr|Used for scripting only. When an error is encountered, DiskPart continues to process commands as if the error did not occur. Without this parameter, an error causes DiskPart to exit with an error.|

## Remarks

-   After you create the volume, the focus automatically shifts to the new volume.

## <a name="BKMK_examples"></a>Examples
To create a mirrored volume of 1000 megabytes in size, on disks 1 and 2, type:

```
create volume mirror size=1000 disk=1,2
```

#### Additional references
[Command-Line Syntax Key](Command-Line-Syntax-Key.md)

[Diskpart \[LH\]](assetId:///26a4a166-95fa-4faf-95bc-2d5345f4a57a)

