---
layout: default
title: DSC 180A Methodology Assignment 4
---

# DSC 180A Methodology Assignment 4

**Name:** Nicolas Toon

**Email:** [nitoon@ucsd.edu](mailto:nitoon@ucsd.edu)

**Section:** D43 - AI-Powered Cloud Microscopy for Growing Mini-Organs in the Lab

**Mentor:** Reem Khojah

---

**1. What is the most interesting topic covered in your domain this quarter?**

The most interesting topic we covered in our domain this quarter was organoid growth. Organoids are three-dimensional cell cultures, typically grown from stem cells, that self-organize into structures 
resembling miniature versions of real organs. What I found most fascinating is how many visible signs of growth and development there are, and how much those morphological features can tell us about 
whether an organoid is developing healthily. Two examples are infolds and rosettes. Infolds occur when the tissue layer folds inward on itself, which is a crucial sign for healthy development. It shows 
that the expanding tissues are maximizing their surface area in which they can grow. Rosettes signal that the cells are organizing into structured, functional tissue instead of clumping randomly.

**2. Describe a potential investigation you would like to pursue for your Quarter 2 Project.**

For my Quarter 2 Project, I would like to build an automated computer vision pipeline that identifies organoids with infolds/rosettes (or lack thereof), and then reports on how the organoids are developing 
inside the well. 
Right now, assessing organoid growth depends on someone manually inspecting images, which can be extremely time-consuming and subjective to the researcher analyzing the cells. An automated pipeline would 
make this assessment faster and more consistent.

The automated pipeline would consist of three stages:

1. **Organoid segmentation.** A segmentation model would detect and isolate each organoid as it passes through the camera's field of view, separating it from the background and from neighboring organoids.
   This gives us a clean region of interest for each one and lets us crop out each organoid to get a closer look at its characteristics.
3. **Feature segmentation.** A second segmentation model would run on each isolated organoid to locate infolds/rosettes. Each organoid would then be labeled as having or not having each feature, along with
   where the feature appears and how large it is.
5. **Population analysis and reporting.** The final stage would aggregate the results across all organoids: how many have infolds/rosettes, and how these measurements change over time. From these statistics,
   the pipeline would automatically generate a report describing what was observed.

A key challenge will be getting enough labeled data, since infolds/rosettes can be small and look very different between organoids.

**3. What is a potential change you'd make to the approach taken in your current Quarter 1 Project?**

Our Quarter 1 project is a prototype of the pipeline described above, and because it is a first pass, we explored many options at once without going deep on any of them. The change we would make is to 
become more confident in our design choices and commit to them, rather than continuing to experiment broadly with different architectures, preprocessing steps, and augmentation strategies. Spreading our 
effort across many ideas, especially with limited resources, makes it hard to determine which is the absolute best method. I think that finding the best method isn't as important as choosing one "good enough" 
method and committing to it. In other words, I want to settle on a reasonable baseline and continue to work in iterative cycles. The goal is to move from a prototype that shows the pipeline is possible to a 
more focused, well-understood system.

**4. What other techniques would you be interested in using in your project?**

Three techniques that sound interesting for the project are pretrained encoders, morphological feature extraction, and time-series analysis. Pretrained encoders, trained on large image or microscopy datasets, 
have already learned general features like edges, textures, and shapes, so using one as the backbone of our segmentation models could give us pretty good performance with not that much labeled data. 
Morphological feature extraction would turn each segmentation mask into quantitative measurements such as area, perimeter, circularity, and solidity. Time-series analysis would then track how these measurements 
change over the growth period, showing when infolds/rosettes first appear and helping us characterize typical growth trajectories and alert us about organoids that seem to be developing incorrectly or dying.
