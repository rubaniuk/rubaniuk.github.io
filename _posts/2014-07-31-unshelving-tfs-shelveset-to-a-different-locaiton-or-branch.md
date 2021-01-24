---
# id: 307
title: Unshelving TFS shelveset to a different location or branch
date: 2014-07-31T08:38:53-07:00
author: andrei
layout: post
# guid: http://www.rubaniuk.com/?p=307
# permalink: /?p=307
categories:
  - Software Development
---
  1. Install <a title="Microsoft Visual Studio Team Foundation Server 2013 Power Tools" href="http://visualstudiogallery.msdn.microsoft.com/f017b10c-02b4-4d6d-9845-58a06545627f" target="_blank">Microsoft Visual Studio Team Foundation Server 2013 Power Tools</a>, then open command line and cd into a location where you have your TFS workspace otherwise TFTP will show error <pre class="brush: bash; gutter: true">C:\Windows\System32&gt;tfpt unshelve
Unable to determine the workspace.</pre>

  2. Run tfpt unshelve /? <pre class="brush: bash; gutter: true">c:\Source\Project\tfpt&gt;unshelve /?
tfpt unshelve - Unshelve into workspace with pending changes

This command has two separate modes of operation:

1. Migrate: allows migration of shelved changes from one branch into another
   by rewriting server paths.

2. Undo: allows changes from an already-unshelved shelveset to be undone,
   cleaning up pending adds, and preserving other existing pending changes in
   the workspace.

Usage: tfpt unshelve /migrate /source:serverpath /target:serverpath
                     [shelvesetname[;username]] [/backup]

       tfpt unshelve /undo shelvesetname[;username] [/batchsize:num]
                     [/recursive] [filespec...]

 shelvesetname          The name of the shelveset to unshelve
 /backup                Creates a backup shelveset
 /migrate               Rewrite the server paths of the shelved items
                        (for example to unshelve into another branch)
 /source:serverpath     Source location for path rewrite (supply with /migrate)
 /target:serverpath     Target location for path rewrite (supply with /migrate)
 /undo                  Undo pending changes from an unshelved shelveset
 /batchsize:num         Set the batch size for server calls (default 500)</pre>

  3. The option you need to execute is **unshelve /migrate**. Specify **/source**, **/target** and **shelvesetname** &#8211; that should be enough. You may need to resolve conflicts, in most cases AutoMerge in the pop up dialog will do the trick.

&nbsp;