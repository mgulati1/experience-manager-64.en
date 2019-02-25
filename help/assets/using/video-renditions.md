---
title: Video renditions
seo-title: Video renditions
description: null
seo-description: null
uuid: 70929121-10a0-450a-b48c-80a7bd6cf465
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: managing-assets
content-type: reference
discoiquuid: 22599969-2a36-40f6-97b2-d23b3c86690b
index: y
internal: n
snippet: y
---

# Video renditions{#video-renditions}

Adobe Experience Manager (AEM) Assets generates video renditions for video assets of various formats including OGG, FLV, and so on.

AEM Assets supports static and dynamic renditions (DM-encoded renditions) for media assets.

Static renditions are generated natively using FFMPEG (installed and available on the system path) and stored in the content repository.

The DM-encoded renditions are stored in the proxy server and served at runtime.

AEM assets provide playback support for these renditions on the client side.

To view the renditions of a particular video asset, open its asset page, and click/tap the GlobalNav icon. Then, choose **Renditions** from the list.

![](assets/chlimage_1-484.png)

The list of video renditions are displayed in the** Renditions** panel. 

![](assets/chlimage_1-485.png)

To configure the proxy server for DM-encoded renditions, [configure Dynamic Media Cloud services.](../../assets/using/config-dynamic.md)

To generate video renditions with desired parameters, [create a corresponding video profile](../../assets/using/video-profiles.md).

After you configure the proxy server and create video profiles, you can include this video preset in a processing profile and apply the processing profile to a folder.

>[!NOTE]
>
>Audio playback do not work for OGG and WAV files on Internet Explorer 11. An error "Invalid Source " shows up on the asset details page for assets with extension OGG or WAV.
>
>On MS Edge and iPad , OGG files do not play and raise an Unsupported format error.
