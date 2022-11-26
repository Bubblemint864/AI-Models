# 2x_Bubble_AnimeScale_SwinIR_Small_v1
## Images
| Input | Output | imgsli | slow.pics |
:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|
![](http://bubblemint.cumz.one/5A555q1.png) | ![](http://bubblemint.cumz.one/9hZLtrs.png) | https://imgsli.com/MTM2MDk5 | https://slow.pics/c/ZhQUdVeW
![](http://bubblemint.cumz.one/evNPm8p.png) | ![](http://bubblemint.cumz.one/4Gqvqam.png) | https://imgsli.com/MTM2MTAx | https://slow.pics/c/JYeYs82N
![](http://bubblemint.cumz.one/4zdAV3V.png) | ![](http://bubblemint.cumz.one/7UXS9ha.png) | https://imgsli.com/MTM2MTAy | https://slow.pics/c/4hRVpQtQ
![](http://bubblemint.cumz.one/9hdKirn.png) | ![](http://bubblemint.cumz.one/8aUFjnK.png) | https://imgsli.com/MTM2MTAw | https://slow.pics/c/GdttvM6r
![](http://bubblemint.cumz.one/129e2dq.png) | ![](http://bubblemint.cumz.one/AfZnxSm.png) | https://imgsli.com/MTM2MTAz | https://slow.pics/c/A8E9Jaj2 
## Videos
| Input | Output |
|:-----:|:------:|
[<img src="http://bubblemint.cumz.one/5JQnyMZ.png" width="100%">](http://bubblemint.cumz.one/7DsKBML.mp4 "540p") |[<img src="http://bubblemint.cumz.one/9wweL9D.png" width="100%">](http://bubblemint.cumz.one/4SAHakz.mp4 "1080p")
[<img src="http://bubblemint.cumz.one/3GmxEyL.png" width="100%">](http://bubblemint.cumz.one/5c5NhKW.mp4 "540p") |[<img src="http://bubblemint.cumz.one/51S6JFd.png" width="100%">](http://bubblemint.cumz.one/6FQC1Qz.mp4 "1080p")
[<img src="http://bubblemint.cumz.one/yi9jt7D.png" width="100%">](http://bubblemint.cumz.one/829iXBq.mp4 "540p") |[<img src="http://bubblemint.cumz.one/59xY5ke.png" width="100%">](http://bubblemint.cumz.one/7vC8Btj.mp4 "1080p")

This model was trained to attempt to faithfully upscale low resolution anime images with minimal contrast shifting.

I used what I learnt from training [2x_Bubble_AnimeScale_Compact](https://github.com/Bubblemint864/AI-Models/blob/main/Real-ESRGAN/2x_Bubble_AnimeScale_Compact/v1/Overview.md) to train a model that would look significantly better. AnimeScale_Compact was very fast, and for the speed I was pretty happy with the results; however, it had a few major flaws. Due to the contrast shifting that occured (for unknown reasons), it would often give images an "overexposed" look which would ruin skin tones on bright scenes and the dataset lacked diversity, which resulted in the model only performing well at 540p. I attempted to retrain AnimeScale_Compact with a new dataset but I kept getting identical results. So I gave up on training Compact and switched to SwinIR. While yes it is very slow and VRAM hungry, the results are good - and that's what matters the most to me. Contrast shifting is significantly reduced and it avoids the waterpaint effect much more compared to AnimeScale_Compact. However, due to limitations with SwinIR Small, it seems to produce rainbow artefacts on very low resolution or highly compressed images.

The dataset consists of 1042 SFW & NSFW Anime frames sourced directly from their respective Blu Ray discs. These were then batch compressed with x264/vp9/mpeg2/x265 using randomised CRF values ranging from 0-40. After this I added some blur into the dataset to slightly sharpen the results and I downscaled and resized a small portion of images so that the model can somewhat handle sources with poor scaling. Then lastly I used [chaiNNer](https://github.com/chaiNNer-org/chaiNNer) to batch average colour fix the low quality frames. You may notice that the model adds a bit of grain to the output, this is most likely because some of the frames in the dataset had grain on them and I did not add extra grain to the low quality frames for the AI to learn how to remove. This isn't necessarily a bad thing as having a slight amount of grain gives the image a more natural look overall.

Overall I'm very happy with this model!

Special thanks to `Kim#9859` and `musl#0800` from the [Enhance Everything](https://discord.gg/cpAUpDK) server for helping me. This would not have been possible without you guys!
