---
# id: 201
title: 'Visual Studio 2012: Project is missing TFS status icon'
date: 2013-08-27T11:02:25-07:00
author: andrei
layout: post
# guid: http://www.rubaniuk.com/?p=201
# permalink: /?p=201
categories:
  - Software Development
---
Recently I had an annoying issue: C# project checked-in into TFS was added to Visual Studio 2012 solution and was lacking TFS status icon in Solution Explorer:

<div id="attachment_202" style="width: 408px" class="wp-caption aligncenter">
  <a href="http://www.rubaniuk.com/wp-content/uploads/2013/08/VisualStudio2012_NotInTFS.png" target="_blank"><img aria-describedby="caption-attachment-202" loading="lazy" class="size-full wp-image-202 " alt="Missing TFS Status" src="http://www.rubaniuk.com/wp-content/uploads/2013/08/VisualStudio2012_NotInTFS.png" width="398" height="59" srcset="https://www.rubaniuk.com/wp-content/uploads/2013/08/VisualStudio2012_NotInTFS.png 398w, https://www.rubaniuk.com/wp-content/uploads/2013/08/VisualStudio2012_NotInTFS-300x44.png 300w" sizes="(max-width: 398px) 100vw, 398px" /></a>
  
  <p id="caption-attachment-202" class="wp-caption-text">
    Missing TFS Status
  </p>
</div>

Turns out the fix to this issue is very simple:

  1. In VS2012 Menu go to File > Source Control > Advanced > Change Source Control
  2. In Change Source Control window select project that was missing TFS Status icon, it has Not Controlled status 
    <div id="attachment_203" style="width: 998px" class="wp-caption aligncenter">
      <a href="http://www.rubaniuk.com/wp-content/uploads/2013/08/VisualStudio2012_NotInTFS2.png" target="_blank"><img aria-describedby="caption-attachment-203" loading="lazy" class="size-full wp-image-203 " alt="Change Source Control" src="http://www.rubaniuk.com/wp-content/uploads/2013/08/VisualStudio2012_NotInTFS2.png" width="988" height="446" srcset="https://www.rubaniuk.com/wp-content/uploads/2013/08/VisualStudio2012_NotInTFS2.png 988w, https://www.rubaniuk.com/wp-content/uploads/2013/08/VisualStudio2012_NotInTFS2-300x135.png 300w, https://www.rubaniuk.com/wp-content/uploads/2013/08/VisualStudio2012_NotInTFS2-624x281.png 624w" sizes="(max-width: 988px) 100vw, 988px" /></a>
      
      <p id="caption-attachment-203" class="wp-caption-text">
        Change Source Control
      </p>
    </div></li> 
    
      * Click Bind
      * Save your solution and check it in into TFS.
      * Done!</ol> 
    
    &nbsp;