# 2x_Bubble_AnimeScale_Compact_v1

| Input | Output | imgsli | slow.pics |
:-------------------------:|:-------------------------:|:-------------------------:|:-------------------------:|
![](http://bubblemint.cumz.one/2Novf7f.png)  |  ![](http://bubblemint.cumz.one/3E3s1Up.png) | https://imgsli.com/MTM0MTkw | https://slow.pics/c/Y0AaOa3e

This model was trained to attempt to upscale low resolution anime images with less detail loss compared to the [AnimeVideoV3](https://github.com/xinntao/Real-ESRGAN/blob/master/docs/anime_video_model.md) model by [xinntao](https://github.com/xinntao/).

This is the first model I've ever trained, so it's far from perfect, but I believe it's worthy of release. It scales quite nicely while avoiding the [AnimeVideoV3](https://github.com/xinntao/Real-ESRGAN/blob/master/docs/anime_video_model.md) model's notorious deblur problems, and it avoids the waterpaint effect that is present in that model if the input is decent. The waterpaint effect still occurs if the input image is of poor quality, as shown in the table above, though I believe this is a limitation of compact. The model also suffers from a slight bit of haloing due to me messing up the dataset half way through the training process, hopefully this can be addressed in a later revision of the model.

I extracted 1,845 anime frames from various Blu Ray discs and web releases to create the dataset. These were used for the HQ reference images and were left untouched without further filtering. I used a variety of techniques to create the LQ images. The LQ set is mostly made up of images from the HQ set that were randomly downscaled using the area, bicubic, bilinear, lanczos, and neighbor scaling algorithms. I then used a combination of gaussian blur, noise, and x264/mpeg2/vp9 compression on some of those frames. I previously stated that halfway through, I messed up the dataset by introducing too much uniform noise into it. As training progressed, I degraded more images to help with compression removal. As a result, the model learned how to remove some artefacts and blocking - but it still struggles to remove banding, which I believe is a limitation of compact. Relating to compact, I was not able to mitigate artefacts caused by compact, so you may see green/pink artefacts on some images.

It took around 2 days of training and 1,350,000 iterations to get to the final model. I have included previous iterations in this repository as they may/may not suffer from less problems and possibly might suit your needs more.

In conclusion, I think that this is a good start - and I can't wait to train more models. This has been a fun learning experience! :D

Special thanks to `Kim#9859` and `musl#0800` from the [Enhance Everything](https://discord.gg/cpAUpDK) server for helping me. This would not have been possible without you guys!
