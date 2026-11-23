← [论文索引](../INDEX.MD)

# Appendix · Where induction heads form

In this section we examine: Where are induction heads located in models? Do they generally form in the second layer, or the last layer, or somewhere else?

## Small attention-only models

In our attention-only models, induction heads form in the last layer.

(In these plots, each point represents a head, colored by layer and arranged along the x-axis by depth in the model. Th height of the point is the prefix matching score of that head.)

![](../images/e9dd2c7bbcae43f3905a5487e1291249c162453b08f1818c3d898234199b4069.jpg)

![](../images/1f5eb75426bf4524f11085c9c0140e3495544fdf34eeafb1c6b71741334a2366.jpg)

![](../images/08b0ba991dce7ba96d4d0ec2c06b018b81bdd23f831c583d92a80ec377203b29.jpg)

![](../images/ba4338321ae96821b373d781f71fcd608f0780cfeb9dd14028bd39264d8f3cf5.jpg)  
Small models with MLPs:

![](../images/c53476b806bde7f7f9b59b392b7c8194b9ae37754a3a52d2a894362ff6876931.jpg)

![](../images/915ddd05f6c2cc1de3438854daa3d647ff7cfa88c65e9db1bf7f80549e688ef1.jpg)

In small models with MLPs, by the 5L and 6L size, the induction heads form more in the <sub>secon</sub>d-t<sub>o</sub>-l<sub>as</sub>t layer  
![](../images/2bc1fec520d0cc060da29aeb969eb7c14876202b77c03d31c892be06acfa306c.jpg)

![](../images/c89be8916929365920c5b560151e1a23921b331436f9e755ffe9f65c6c6845e5.jpg)

![](../images/b58bdb1e4e356fe8d898bf9a3f972d31c3a17f663eb04e47a9c8ea42e74d3ec7.jpg)

![](../images/b257de6b6bd74d06876974e1b6ba94fce7682686e196bfc4b0c6961d63a738cf.jpg)

![](../images/1ffd0c6e39886d414645255f5dbef790e7eddb9cd5c3f2915b5624f457773812.jpg)

![](../images/f7462552b7ca13ca274914bb6e5a35412ec624e0d427ac8b87653a9c582684b7.jpg)

## Full-scale models:

In the models in our full-scale sweep, induction heads form earlier. In fact, in 24L and 40L models the majority of induction heads form before the halfway point in model depth.

Note that in these plots, only a randomized sample of 100 heads (with selection biased towards those scoring highly on prefix matching) are shown as opaque dots; most of the datapoints are left translucent for ease of reading.

![](../images/ab33f3c3e479dbd9dcb4bd364dc0725b2fe0f85e19f15f1d1994e3bf9497bf34.jpg)

![](../images/896abd09dcc36e49adfcfc1e05b87adbbb2fe181bc13f8fd6924957af48d087c.jpg)

![](../images/c87dbf1c9f61277a139ee1718185e97c4b7335f7be528cfc7d13bd39a6637f0f.jpg)

![](../images/10cdb11e421d726f18a4f9b435321321e8e031ce48bf33a1c47d33f80bba4544.jpg)

![](../images/0abdb6ca65fb50d8b22faa8585f21c2ca505ce31924716c157debb0e5f536459.jpg)

![](../images/ccba65100603c2cbf65e250342988b6a8a9d8e4b6f60161a4d332800efcc8802.jpg)

