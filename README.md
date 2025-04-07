# Resistometer

On April 5, 2025, protesters across the US marched in opposition to Donald Trump's multiple offenses against the constitution. Media reports of the event contained participation estimates that varied wildly.

> "While crowd sizes are difficult to estimate, organizers said that more than 600,000 people had signed up to participate 
> and that events also took place in U.S. territories and a dozen locations across the globe."
Shaila Dewan, Minho Kim and Katie Benner
_Mass Protests Across the Country Show Resistance to Trump_  
April 5, 2025  
[New York Times](https://www.nytimes.com/2025/04/05/us/politics/anti-trump-protests-hands-off.html)

> "CNN has not been able to independently verify how many people attended Saturday’s demonstrations, 
> but 'Hands Off!' organizers say that 'millions' of people turned up from coast to coast."  
Alaa Elassar, Shania Shelton and Mina Allen  
_‘Hands Off!’ protesters across US rally against President Donald Trump and Elon Musk_  
April 6, 2025  
[CNN](https://www.cnn.com/2025/04/05/us/hands-off-protests-trump-musk/index.html)

> "Yesterday was incredible. The official count is in — 5.2 million people joined the #HandsOff protest nationwide. 
> So many are asking: what’s next? Mark your calendars: 4/19 is the next nationwide day of protest."
Alt National Park Service  
April 6, 2025  
[Bluesky](https://bsky.app/profile/altnps.bsky.social/post/3lm5nnz5ook2q)

Uncertainty in these estimates provides an opportunity for people who want to minimize the scale of participation or invent conspiracy theories about paid protestors. Conversely, confident estimates can help recruit new supporters who are emboldened to join a broad and growing coalition of citizens who are speaking out.

This project aims to collect a set of data and tools to make rapid, reliable crowd size estimates in the open.

# Methodology

There are a number of methods for estimating the size of large crowds at a protest. A few of them are:

* Jacob's method
  * Organizers divide the event area into sections, estimate the average number of people per section, and multiply that by the total number of sections occupied.
* Cell phone data analysis
  * A large technology company with an application with location permissions installed on a large sample of phones can produce crowd size estimates by counting the number of phones observed at the protest location during the protest time. These estimates can be weighted by known biases in the population running the app compared to the overall population.
* Analysis of event photographs
  * Photos taken at the event which capture large portions of the event space can be used to count participants after the fact. This process can be scaled by using computer vision algorithms designed to estimate the number of people present in an image.

This project will focus on collecting and organizing aerial photographs of the protests and applying computer vision techniques to produce crowd size estimates. This will include attempting to verify the authenticity of photographs (i.e. that they were captured at the correct time and location for a known protest), as well as attempting to avoid double counting by mapping photographs to unique geographic extents.

# Crowd Counting Literature

These resources contain useful information for getting up to speed on crowd counting, which are methods of estimating crowd size from imagery.

[Deep Learning in Crowd Counting: A Survey](https://ietresearch.onlinelibrary.wiley.com/doi/10.1049/cit2.12241)  
A survey of crowd counting methodologies from June 2023. This source helpfully includes a summary of academic test datasets used to train and evaluate new models. Following is an excerpt from the table including all of the "hyperscale" datasets. These are datasets whose images include > 1000 subjects.

|Dataset|Number|H|W|Total|Min|Average|Max|APO|Years|Scale of dataset|
|-------|------|-|-|-----|---|------|----|---|-----|----------------|
|JHU-CROWD|4250|900|1450|1114785|-|262.3|7286|70.6|2019|Hyper|
|GTA head|5098|1080|1920|1732505|-|340|-|78.1|2022|Hyper|
|JHU-CROWD++|4372|910|1430|1515005|-|346.5|25791|61.3|2020|Hyper|
|NWPU-crowd|5109|2311|3383|2133238|0|418.5|20033|136.8|2020|Hyper|
|Crowd-saliency|107|576|720|45000|58|421.6|2201|31.4|2016|Hyper|
|CrowdX|24000|768|1024|2400|-|500|-|39.7|2022|Hyper|
|ShanghaiTech part A|482|589|868|241677|33|501.3|3139|31.9|2016|Hyper|
|GCC |15211|1080|1920|7625843|0|501.4|3995|64.3|2019|Hyper|
|UCF-QNRF |1535|2013|2902|1251642|49|815.4|12865|84.7|2018|Hyper|
|UCF_CC_50|50|2888|2101|63974|94|1280.5|4543|68.9|2013|Hyper|
|DLR-ACD |33|-|-|226291|285|6857.3|24368|-|2019|Hyper|



[Awesome Crowd Counting](https://github.com/gjy3035/Awesome-Crowd-Counting)  
A leaderboard showing a large number of models across various test data sets. As of 2025-4-7 `CrowdDiff` has the best performance across many test categories, including the hyperscale test sets we're interested in.

CrowdDiff [code](https://github.com/dylran/crowddiff) | [paper](https://openaccess.thecvf.com/content/CVPR2024/papers/Ranasinghe_CrowdDiff_Multi-hypothesis_Crowd_Density_Estimation_using_Diffusion_Models_CVPR_2024_paper.pdf)  
Code and instructions for executing the CrowdDiff model. Unfortunately, this code differs from the methodology described in the related paper, and the link to pre-trained weights is broken as of writing.

GauNet [code](https://github.com/zhiqic/Rethinking-Counting) | [paper](https://arxiv.org/pdf/2206.05253) | [docker](https://hub.docker.com/r/skokec/dau-convnet)

SASNet [code](https://github.com/TencentYoutuResearch/CrowdCounting-SASNet) | [paper](https://ojs.aaai.org/index.php/AAAI/article/view/16360)

CSRNet [code](https://github.com/leeyeehoo/CSRNet-pytorch) | [weights](https://huggingface.co/rootstrap-org/crowd-counting)

TinyCount [code]() | [weights](https://drive.google.com/drive/folders/1dSrFRwqggoSdfMJMI7tLbdluFIDHOnNF) | [paper](https://link.springer.com/article/10.1007/s11554-024-01531-8)
Proximal Mapping Loss [code](https://github.com/Elin24/pml) | [paper](https://openreview.net/forum?id=7p8CcxP1Xc)  
This new methodology is scheduled to be presented at ICLR2025 which is Apr 24 2025.

[Crowd Counting: A Survey](https://www.rootstrap.com/blog/crowd-counting-a-survey)  
A more accessible overview of crowd counting techniques. 
