# 2x_Bubble_AnimeScale_Compact_v1
## Images
| Input | Output | imgsli | slow.pics |
:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|
![](http://bubblemint.cumz.one/2Novf7f.png)  |  ![](http://bubblemint.cumz.one/3E3s1Up.png) | https://imgsli.com/MTM0MTkw | https://slow.pics/c/Y0AaOa3e
![](http://bubblemint.cumz.one/41UEsQv.png) | ![](http://bubblemint.cumz.one/7bfjgmh.png) | https://imgsli.com/MTM0MjA3 | https://slow.pics/c/hjtYgiWt
![](http://bubblemint.cumz.one/9HQsU6W.png) | ![](http://bubblemint.cumz.one/9HQsU6W.png) | https://imgsli.com/MTM0MjEw | https://slow.pics/c/2QmPplix
![](http://bubblemint.cumz.one/2Nfnb5p.png) | ![](http://bubblemint.cumz.one/4U8Z7We.png) | https://imgsli.com/MTM0MjA2 | https://slow.pics/c/KzD3ngOu
![](http://bubblemint.cumz.one/2uefvE8.png) | ![](http://bubblemint.cumz.one/2uefvE8.png) | https://imgsli.com/MTM0MjE1 | https://slow.pics/c/4pZ8ZS8V
## Videos
| Input | Output |
|:-----:|:------:|
[<img src="http://bubblemint.cumz.one/4LwZNh5.png" width="100%">](http://bubblemint.cumz.one/7zMtiVe.mp4 "540p") |[<img src="http://bubblemint.cumz.one/46T8QG5.png" width="100%">](http://bubblemint.cumz.one/9U2L6CW.mp4 "1080p")
[<img src="http://bubblemint.cumz.one/8nyJYb4.png" width="100%">](http://bubblemint.cumz.one/4SmJ8GW.mp4 "540p") |[<img src="http://bubblemint.cumz.one/4BJKRmw.png" width="100%">](http://bubblemint.cumz.one/2pV5Mqo.mp4 "1080p")
[<img src="http://bubblemint.cumz.one/6BvnHFK.png" width="100%">](http://bubblemint.cumz.one/7h7gskr.mp4 "540p") |[<img src="http://bubblemint.cumz.one/h3b6pCu.png" width="100%">](http://bubblemint.cumz.one/3p4jAoC.mp4 "1080p")

This model was trained to attempt to upscale low resolution anime images with less detail loss compared to the [AnimeVideoV3](https://github.com/xinntao/Real-ESRGAN/blob/master/docs/anime_video_model.md) model by [xinntao](https://github.com/xinntao/).

This is the first model I've ever trained, so it's far from perfect, but I believe it's worthy of release. It scales quite nicely while avoiding the [AnimeVideoV3](https://github.com/xinntao/Real-ESRGAN/blob/master/docs/anime_video_model.md) model's notorious deblur problems, and it avoids the waterpaint effect that is present in that model if the input is decent. The waterpaint effect still occurs if the input image is of poor quality, as shown in the table above, though I believe this is a limitation of compact. The model also suffers from a slight bit of haloing due to me messing up the dataset half way through the training process, hopefully this can be addressed in a later revision of the model. Sadly due to the nature of downscaling, there is quite a bit of contrast/gamma shifting which I cannot mitigate.

I extracted 1,845 anime frames from various Blu Ray discs and web releases to create the dataset. These were used for the HQ reference images and were left untouched without further filtering. I used a variety of techniques to create the LQ images. The LQ set is mostly made up of images from the HQ set that were randomly downscaled using the area, bicubic, bilinear, lanczos, and neighbor scaling algorithms. I then used a combination of gaussian blur, noise, and x264/mpeg2/vp9 compression on some of those frames. I previously stated that halfway through, I messed up the dataset by introducing too much uniform noise into it. As training progressed, I degraded more images to help with compression removal. As a result, the model learned how to remove some artefacts and blocking - but it still struggles to remove banding, which I believe is a limitation of compact. Relating to compact, I was not able to mitigate artefacts caused by compact, so you may see green/pink artefacts on some images.

It took around 2 days of training and 1,355,000 iterations to get to the final model. I have included previous iterations in this repository as they may/may not suffer from less problems and possibly might suit your needs more.

In conclusion, I think that this is a good start - and I can't wait to train more models. This has been a fun learning experience! :D

Special thanks to `Kim#9859`, `musl#0800` and `twittman#3594` from the [Enhance Everything](https://discord.gg/cpAUpDK) server for helping me. This would not have been possible without you guys!
