---
title: "Creating a Reproducible Workflow in R"
author: ~
date: '2017-04-21'
slug: ''
categories: ["R"]
tags: ["R", "RStudio", "git", "Github"]
draft: no
---

For starters, I'm happy to say that I fixed the website build error I had mentioned in my first blog post. After plenty of head scratching, rereading the tutorial, and staring at my `config.toml` file, I finally realized I had a tiny typo in my `publishDir` file path, which prevented the documents from being copied to their new folder as expected. \*facepalm\*. I'm not sure how I managed to miss it the first time, but I'm glad to have it fixed now.

---

Having just started learning R last fall, it's awesome to see how much I've learned in a short time. Though I was skeptical of R at first and nervous about its steep learning curve, I got past those reservations quickly, and some of my initial frustrations with learning it now seem trivial. I specifically remember being frustrated about sharing my code within an analysis document. I tried copying and pasting my R code into a Word document (sacrilege, I now know), and was frustrated that it did not preserve the code formatting. *But SAS does that!*, I remember thinking. Thankfully, RStudio has made an easy fix to this problem with RMarkdown documents, plus a variety of other tools to make data analysis easy from start to finish. 

Through learning RMarkdown, I became interested in the idea of reproducible research. In my undergrad program in Applied Economics, the importance of replicability was often stressed, particularly after the Reinhart-Rogoff debacle with their Excel spreadsheet came to light. However, my limited quantitative work with replicability mostly centered around saving my SAS scripts and writing a 'codebook' in Word to document the changes I was making and steps of my analysis. This is not a bad setup, but certainly not very efficient or easily reproducible. Now that I'm comfortable with RStudio, I have embraced the tools they've provided to make an integrated, reproducible workflow all within RStudio, from data intake to report writing.

There are plenty of books and tutorials for the various tools RStudio provides, including RMarkdown, LaTeX integration, and git/Github. I really enjoyed the book [Reproducible Research in R and RStudio](https://www.amazon.com/Reproducible-Research-Studio-Second-Chapman/dp/1498715370/ref=dp_ob_title_bk) by Christopher Gandrud for a complete walkthrough of a reproducible workflow.

Rather than reinvent that wheel, I'd just like to share a few key things that I've learned for a generally reproducible workflow in RStudio and a couple great references for those ideas. These can change somewhat depending on your specific needs and project size, but they work well for me!

## Embrace the Project Structure

Among my first noob mistakes when I began learning R was to put all my R scripts in one folder, all my datasets in another folder, and my written reports in another folder, even from different projects. As you can imagine, this quickly became a confused mess, and it was very difficult to find the files I needed. Thankfully, I quickly caught on to RStudio's idea of 'Projects', so I could keep things organized on a project-by-project basis, whether that's a small class assignment or a large collaborative term project. 

## Incorporate Git/Github

Though understanding git's system of version control seems overwhelming and complicated at first, the fact that most of its functionality exists within a few commands (`pull`, `add`, `commit`, and `push`, namely) definitely helps! Even for small projects where version control may seem unnecessary, using git and hosting your project on Github or another online repo makes it really easy to keep a backup copy for later. Plus, it's an easy way to share your ongoing projects, like this website! RStudio has integrated git and Github functionality, so you can do your push, pull, and commits all from within RStudio. Though some tasks with the command line still make sense, if you're just doing a simple commit and push, you can do that within RStudio with just a couple clicks! I've found it's easiest to set up the Github repo at the beginning of a project, though it is possible to sync an existing project to Github and add git version control after it's begun.

For more information on incorporating git into RStudio, I'd recommend checking out [Happy Git and GitHub for the useR](http://happygitwithr.com/) by Jenny Bryan.

## Divide and Conquer

Even if you're the only person working on a project, documenting your steps can make it easier for someone to see what you did, or even just to remind a future you looking back on it. Though I first began using R by throwing everything from reading in the data to outputting analysis and visuals into a single R script, I've found it can be hard to follow comments littered throughout the code. 

One thing that's helped is to reduce the size of this "master script" by moving my data cleaning into a separate script, with a name like `data-preparation.R`. This is particularly useful if you have a lot of data cleaning, reshaping, or merging datasets in your analysis. Rather than making your computer re-run the dataset creation each time you run your analysis, use a dataset preparation script to save your data as a csv or similar data file, then run your analysis on that. Similarly, if you have created any verbose functions, consider moving them to a separate script that you can source in your analysis, plus then it will already be saved in its own script for any future analyses.

Separate from the master script, I use R Notebooks or an RMarkdown document for communicating my results. That way, the document has all the code necessary to recreate my analysis embedded in it, without adding the extra code from the script that I may want to save, but isn't directly useful or necessary in my report.

Additionally, now that RStudio has released its R Notebooks as of a few months ago, I now sometimes use a 'master notebook' instead of a master script. Similar to Jupyter Notebooks, they offer iterative computing for experimenting with code chunks, written comments for discussing your analysis, and include output and visualizations right below each code chunk. It's got all the benefits of writing a report with RMarkdown, but faster because you don't have to re-knit your document to see how your output changes. R Notebooks can also easily be compiled into HTML, PDF, or Word documents to share your work. If you want to know more about R Notebooks, RStudio has [a great introduction](http://rmarkdown.rstudio.com/r_notebooks.html).

---

Those are some of my main ways of creating a reproducible workflow in RStudio. Of these ideas, using R Notebooks and RMarkdown documents to keep my code and analysis together have been the most useful for me. I'm sure my process will change and improve over time and as RStudio rolls out new features, but this general structure has worked well for me so far. The exact structure of a reproducible workflow will depend on the complexity of task at hand, and you may not be able to share everything on Github if you're dealing with confidential information, but creating a reproducible workflow will help others understand your methods and help yourself in the future when looking back on your previous work!