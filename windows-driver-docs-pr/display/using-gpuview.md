---
title: Using GPUView
description: Using GPUView
ms.assetid: 55f589fd-e3ea-4fd2-9e8d-c225c2c3dbb5
ms.date: 01/23/2019
ms.localizationpriority: medium
---

# Using GPUView


GPUView (*GPUView.exe*) is a development tool for determining the performance of the graphics processing unit (GPU) and CPU. It looks at performance with regard to direct memory access (DMA) buffer processing and all other video processing on the video hardware. GPUView is useful for developing display drivers that comply with the Windows Vista display driver model. GPUView is introduced with the release of the Windows 7 operating system.

GPUView and other files that are associated with it are included with the Windows Performance Toolkit (WPT) as an installable option of the WPT MSI. GPUView binaries are available for x86-based, x64-based, and IA64-based architectures. For example, *Wpt\_x86.msi* is for an x86 platform. 

You can also download GPUView as part of the Windows 7 SDK. After installing the SDK you will need to go to C:\Program Files\Microsoft SDKs\Windows\v7.0\bin and run either wpt_x64.msi or wpt_x86.msi. This will install the Windows Performance Toolkit which contains GPUView. 

The WPT MSI includes the files that are described in the following table.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Files</th>
<th align="left">Purpose</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><em>EULA.rtf</em></p></td>
<td align="left"><p>Legal agreement</p></td>
</tr>
<tr class="even">
<td align="left"><p><em>GPUView.chm</em></p></td>
<td align="left"><p>GPUView help file</p></td>
</tr>
<tr class="odd">
<td align="left"><p><em>Readme.txt</em></p></td>
<td align="left"><p>Any additional information that is not included in the help file</p></td>
</tr>
<tr class="even">
<td align="left"><p><em>GPUView.exe</em></p></td>
<td align="left"><p>Program for viewing ETL files with video data</p></td>
</tr>
<tr class="odd">
<td align="left"><p><em>AEplugin.dll</em>, <em>DWMPlugin.dll</em>, <em>MFPlugin.dll</em>, <em>NTPlugin.dll</em>, <em>DxPlugin.dll</em>, and <em>DxgkPlugin.dll</em></p></td>
<td align="left"><p>Plugins to interpret events</p></td>
</tr>
<tr class="even">
<td align="left"><p><em>CoreTPlugin.dll</em></p></td>
<td align="left"><p>Plugin for Statistical Options dialog</p></td>
</tr>
<tr class="odd">
<td align="left"><p><em>Log.cmd</em></p></td>
<td align="left"><p>Script to turn on and off the appropriate information for logging</p></td>
</tr>
<tr class="even">
<td align="left"><p><em>SymbolSearchPath.txt</em></p></td>
<td align="left"><p>A text file that sets the symbol path to resolve stackwalk and other events</p></td>
</tr>
</tbody>
</table>

To use GPUView, go to the command line and run Log.cmd to start event logging. Then run Log.cmd again to stop logging. This will generate several Event Tracing for Windows (\*.ETL) files; these various streams will all be merged together into a single file called Merged.etl which is what GPUView reads. Some examples of logged events are:

* All CPU context switches, including the stack trace and the reason for switching.
* All kernel mode enters and exits and the stack trace.
* All GPU events as recorded by the DirectX Graphics Kernel, including all command buffer submissions, and resource creation, destruction, lock, and bind events.
* Events reported by the graphics driver, such as command buffer start and end times, and vertical synchronization intervals for each adapter.
* Many other system events that can affect performance, such as page faults.

You can also read ETL files with XPerf (which is likewise part of the Windows SDK), however it will not understand any of the GPU specific events. Because these log files can be relatively large, you can use the `Log m` command instead which will skip many of the very high frequency events.

More information, including how to download and use GPUView, can be found [here](https://graphics.stanford.edu/~mdfisher/GPUView.html). 

 

 





