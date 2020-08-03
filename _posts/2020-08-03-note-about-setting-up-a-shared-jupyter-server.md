---
layout: post
title: Note about setting up a shared Jupyter server
date: 2020-08-03T12:59:11.040Z
tags:
  - Jupyter
  - notebook
  - lab
  - setup
  - enviroment
image: /images/1200px-jupyter_logo.svg.png
---
My company organised a new team of data analysts. One of the requirements that came to me is that they want a Jupyter server. I had set up a Jupyter server before however, that was a few years ago. Things change a lot since then.

So that's that I understand after I did some research.

## Version

There are 3 versions of Jupyter you can install:

<dl>
<dt>1. Jupyter</dt>
<dd>The standalone application run on local PC</dd>
<dt>2. Jupyter Hub</dt>
<dd>A server version of Jupyter supports multiple users and can install on multiple machines</dd>
<dt>3. The Littlest Jupyter Hub (TLJH)</dt>
<dd>A simplified version of Jupyter Hub; Installs on a single machine, but still provide most feature as Jupyter Hub, such as multiple users.</dd>
</dl>
I chose TLJH for my project, the reason is simply: the budget. It is unlikely that the team will need things much more powerful. If your requirement is likely to grow, then Jupyter Hub maybe a better choice.  

It is harder to find documentations for the TLJH, because it is easy to mix up with Jypyter Hub. Now thinking about it, they share many similarities, I should have install Jupyter Hub instead. Well, it's too late. ╮(╯▽╰)╭

The install process can be found from the official documentation, so I am not going into the details.

## UI
There is a new Jupyter UI called Jupyter Lab. Compare to the old Jupyter Notebook, the lab provides a side panel to manage files and plugins. The UI is very similar to the VS code, which is the most popular lightweight editor. I do not use Jupyter much, but I can feel that the lab interface is very powerful especially the ability to install plugins.

![JupyterLab](/images/jupyterlab.png "Jupyter Lab")