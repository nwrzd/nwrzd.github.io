---
title: Use Obsidian to Create Jekyll Blog Posts
date: 2024-09-11  11:09:00 +0400
tags:
  - obsidian
  - jekyll
categories:
  - HowTo
  - Tech
---
This is a simple guide to use Obsidian to draft and publish your Jekyll blog posts.

To setup the workflow, we will be using Obsidian native 'Template' plugin. Steps to setup the workflow is as follows:

**Steps1** : Create a folder within Obsidian where you will create drafts of posts. Let's call this folder 'Blog Drafts'

**Step 2:**  Create a template file within your template folder and name it template-blog. 
- If you are new to the 'templates' plug-in, [read through this guide from obsidian](https://help.obsidian.md/Plugins/Templates){:target="_blank"}
- Insert note [properties](https://help.obsidian.md/Editing+and+formatting/Properties){:target="_blank"} with the following fields: 
  
| Property Fields Name | Property Field Type |           Property Field Value           |
| :------------------: | :-----------------: | :--------------------------------------: |
|        title         |        Text         |      {% raw %}{{title}}{% endraw %}      |
|         date         |        Date         | {% raw %} {{date}} {{time}} {% endraw %} |
|         tags         |        Tags         |                                          |
|      categories      |        List         |                                          |

**Step 3:**  Set a hotkey for 'Insert Template' if not already done. [Read through this guide from obsidian for more details.](https://help.obsidian.md/User+interface/Hotkeys){:target="_blank"}

**Step 4:** Create an bash script to run to sync the obsidian 'Blog Drafts' folder with the \_drafts' folder in Jekyll.  Additionally, if you are like me, you would also want to publish the draft and serve it for local view. Sample script:
```
#!/bin/bash

#Copy draft posts from obsidian into jekyll _drafts folder
rsync -vhr /mnt/d/Laptop-Data/ActiveData/Obsdidan/Personal\ Notes/1.Projects/Content\ Creation/nwrzd.github.io/ ./_drafts/ --delete

#Publish all drafts as posts
jekyll publish ./_drafts/* -f

#Serve the jekyll site locally
jekyll serve
```

Fin! The workflow setup is now complete.

Once you have completed steps 1 through 4, to create a draft blog post, create a new file within 'Blog Drafts'. Apply 'template-blog' as template using the hotkey.  Write your article/blog entry. Update the tag and category fields. Execute the sync script. The newly created draft along with any other drafts will be synced into the \_drafts folder. If you are ready to publish, use Jekyll's workflow to publish the post.

This is the initial iteration of the workflow. Will share updates as it happens.





