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

I've been using Obsidian for note taking and journaling for a couple of years now. I figured that since Jekyll uses markdown for it's pages, might as well use Obsidian to draft the posts as well.

To setup the workflow, I used Obsidian native 'Template' plugin. Steps to setup the workflow is as follows:

**Steps1** : Create a folder within Obsidian where you will create drafts of posts. Let's call this folder 'Blog Drafts'

**Step 2:**  Create a template file within your template folder and name it 'template-blog'. 
- If you are new to the 'templates' plug-in, [read through this guide from obsidian](https://help.obsidian.md/Plugins/Templates){:target="_blank"}
- Add the template note [properties](https://help.obsidian.md/Editing+and+formatting/Properties){:target="_blank"} with the following fields: 
  
| Property Fields Name | Property Field Type |           Property Field Value           |
| :------------------: | :-----------------: | :--------------------------------------: |
|        title         |        Text         |      {% raw %}{{title}}{% endraw %}      |
|         date         |        Date         | {% raw %} {{date}} {{time}} {% endraw %} |
|         tags         |        Tags         |                                          |
|      categories      |        List         |                                          |

**Step 3:**  Set a hotkey to 'Insert Template' if not already done. [Read through this guide from obsidian for more details.](https://help.obsidian.md/User+interface/Hotkeys){:target="_blank"}

**Step 4:** Create and save a bash script to the root of your local Jekyll folder.  Remember to change mode to allow execution. Run the script to sync the obsidian 'Blog Drafts' folder with the \_drafts' folder in Jekyll.
If you are like me, you might also want to auto-publish the draft and serve it for local view. Sample script as follows:
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

To create a draft blog post:
1. Create a new file within 'Blog Drafts' folder in Obsidian. 
2. Apply 'template-blog' as template using the hotkey.  
3. Write your article/blog entry. 
4. Update the tag and category fields. 
5. Execute the sync script. The newly created draft along with any other drafts will be synced into the \_drafts folder. 
6. If you are ready to publish, use Jekyll's workflow to publish the post (if you did not automate publish within the script).
7. Check out your new post on Jekyll.

That's it.

This is the initial iteration of the workflow. Will share updates as it happens.





