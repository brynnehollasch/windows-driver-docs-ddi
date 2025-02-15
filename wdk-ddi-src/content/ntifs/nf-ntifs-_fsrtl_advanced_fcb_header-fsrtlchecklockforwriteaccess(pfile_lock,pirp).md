---
UID: NF:ntifs.FsRtlCheckLockForWriteAccess(PFILE_LOCK,PIRP)
title: FsRtlCheckLockForWriteAccess function (ntifs.h)
description: The FsRtlCheckLockForWriteAccess routine determines whether the process associated with a given IRP has write access to a locked region of a file.
old-location: ifsk\fsrtlchecklockforwriteaccess.htm
tech.root: ifsk
ms.assetid: 549da751-6a28-4d54-995f-dabb9e29ab09
ms.date: 03/29/2018
ms.keywords: FsRtlCheckLockForWriteAccess, FsRtlCheckLockForWriteAccess routine [Installable File System Drivers], fsrtlref_460451fb-37b9-4c7e-bf53-8d72c7e73a55.xml, ifsk.fsrtlchecklockforwriteaccess, ntifs/FsRtlCheckLockForWriteAccess
ms.topic: function
f1_keywords:
 - "ntifs/FsRtlCheckLockForWriteAccess"
req.header: ntifs.h
req.include-header: Ntifs.h
req.target-type: Universal
req.target-min-winverclnt:
req.target-min-winversvr:
req.kmdf-ver:
req.umdf-ver:
req.ddi-compliance:
req.unicode-ansi:
req.idl:
req.max-support:
req.namespace:
req.assembly:
req.type-library:
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <= APC_LEVEL
topic_type:
- APIRef
- kbSyntax
api_type:
- DllExport
api_location:
- NtosKrnl.exe
api_name:
- FsRtlCheckLockForWriteAccess
product:
- Windows
targetos: Windows
req.typenames: VOLUME_READ_PLEX_INPUT, *PVOLUME_READ_PLEX_INPUT
ms.custom: RS5
---

# FsRtlCheckLockForWriteAccess function


## -description


The <b>FsRtlCheckLockForWriteAccess</b> routine determines whether the process associated with a given IRP has write access to a locked region of a file.


## -parameters




### -param FileLock [in]

Pointer to the FILE_LOCK structure for the file. This structure must have been initialized by a previous call to <a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlallocatefilelock">FsRtlAllocateFileLock</a> or <a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlinitializefilelock">FsRtlInitializeFileLock</a>.


### -param Irp [in]

Pointer to the IRP. Must be an IRP for a write operation.


## -returns



<b>FsRtlCheckLockForWriteAccess</b> returns <b>TRUE</b> if the process has write access, <b>FALSE</b> otherwise.




## -remarks



On Microsoft Windows XP and later, <b>FsRtlCheckLockForWriteAccess</b> checks the process to which the thread that requested the write operation is currently attached.

On Microsoft Windows 2000 and earlier, <b>FsRtlCheckLockForWriteAccess</b> checks the process that created the thread.

<b>FsRtlCheckLockForWriteAccess</b> checks to see if there are any conflicting locks in the byte range that is to be written.

<b>FsRtlCheckLockForWriteAccess</b> does not complete the IRP specified by <i>Irp</i>.

Minifilters must call <a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/content/fltkernel/nf-fltkernel-fltchecklockforwriteaccess">FltCheckLockForWriteAccess</a> instead of <b>FsRtlCheckLockForWriteAccess</b>.




## -see-also




<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/content/fltkernel/nf-fltkernel-fltchecklockforwriteaccess">FltCheckLockForWriteAccess</a>



<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlallocatefilelock">FsRtlAllocateFileLock</a>



<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlchecklockforreadaccess">FsRtlCheckLockForReadAccess</a>



<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlfastchecklockforwrite">FsRtlFastCheckLockForWrite</a>



<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlinitializefilelock">FsRtlInitializeFileLock</a>



<a href="https://docs.microsoft.com/windows-hardware/drivers/ddi/content/ntifs/nf-ntifs-_fsrtl_advanced_fcb_header-fsrtlprocessfilelock">FsRtlProcessFileLock</a>
 

 

