---
# id: 433
title: Failed to connect to a Windows service
date: 2016-06-04T11:39:27-07:00
author: andrei
layout: post
# guid: http://www.rubaniuk.com/?p=433
# permalink: /?p=433
categories:
  - Uncategorized
---
Recently I was testing real-world performance of [TP-LINK Archer T9E AC1900](http://www.amazon.com/TP-LINK-Archer-T9E-Beamforming-Low-profile/dp/B00TQEX7AQ) wireless adapter. The experiment was quite unsuccessful and I didn&#8217;t experience any reasonable improvement. Quite the opposite: speeds did not improve but the connection was mush less stable.

After uninstalling TP-Link driver/utility package I&#8217;ve noticed that it left my Windows 10 installation quite messed up:

<img loading="lazy" class="aligncenter size-full wp-image-436" src="http://www.rubaniuk.com/wp-content/uploads/2016/06/Untitled.png" alt="Untitled" width="356" height="115" srcset="https://www.rubaniuk.com/wp-content/uploads/2016/06/Untitled.png 356w, https://www.rubaniuk.com/wp-content/uploads/2016/06/Untitled-300x97.png 300w" sizes="(max-width: 356px) 100vw, 356px" /> 

Really TP-Link? I was not able to use my old USB Wireless Adapter and the list of wireless networks simply wouldn&#8217;t show up. Quick Internet search helped solve the problem, resetting Winsock Catalog fixed it:

<pre class="brush: bash; gutter: true">netsh winsock reset</pre>

<span style="line-height: 24.0001px;">In addition, I suspected that Windows system files might be corrupted so I decided to check:</span>

<pre class="brush: bash; gutter: true">C:\WINDOWS\system32\sfc /scannow

Beginning system scan. This process will take some time.

Beginning verification phase of system scan.
Verification 100% complete.

Windows Resource Protection found corrupt files and successfully repaired
them. Details are included in the CBS.Log windir\Logs\CBS\CBS.log. For
example C:\Windows\Logs\CBS\CBS.log. Note that logging is currently not
supported in offline servicing scenarios.</pre>

All fixed, back to more productive activities.

&nbsp;