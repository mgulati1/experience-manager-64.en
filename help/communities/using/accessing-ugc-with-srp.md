---
title: Accessing UGC with SRP
seo-title: Accessing UGC with SRP
description: When a site is configured to use ASRP or MSRP, the actual UGC is not be stored in AEM's node store (JCR)
seo-description: When a site is configured to use ASRP or MSRP, the actual UGC is not be stored in AEM's node store (JCR)
uuid: 67f3d3ef-eca1-42b6-8395-fde51537e95c
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 5c3ae896-85de-42ef-a476-25d22d2db98d
index: y
internal: n
snippet: y
---

# Accessing UGC with SRP{#accessing-ugc-with-srp}

## About SRP {#about-srp}

All AEM Communities components and features are built on the [social component framework (SCF)](../../communities/using/scf.md), which invokes the SocialResourceProvider API to access all user generated content (UGC).

Before a community site is created, the [storage resource provider (SRP)](../../communities/using/working-with-srp.md) must be configured to select an implementation consistent with the underlying [topology](../../communities/using/topologies.md). The SRP implementations are based on three storage options :

1. [ASRP](../../communities/using/asrp.md) - Adobe on-demand storage
1. [MSRP](../../communities/using/msrp.md) - MongoDB
1. [JSRP](../../communities/using/jsrp.md) - JCR

## About UGC Storage {#about-ugc-storage}

What is important to know about storage of UGC is, when a site is configured to use ASRP or MSRP, the actual UGC is not be stored in AEM's [node store](../../sites/deploying/using/data-store-config.md) (JCR).

While there may be nodes in JCR which shadow the UGC to provide useful metadata, these nodes are not to be confused with the actual UGC.

See [Storage Resource Provider Overview.](../../communities/using/srp.md)

## Best Practice {#best-practice}

When developing custom components, developers should be careful to code independently of the current chosen topology, thus retaining flexibility to move to a new topology in the future.

### Assume JCR Not Available {#assume-jcr-not-available}

Methods specific to JCR should avoided.

Methods to use :

* Sling API (Sling Resource)

    * do not assume there are JCR nodes

* OSGi Events

    * do not assume there are JCR events

* [SocialResourceUtilities](../../communities/using/socialutils.md#socialresourceutilitiespackage)
* [SCFUtilities](../../communities/using/socialutils.md#scfutilitiespackage)

Methods to avoid :

* Node API
* JCR events
* workflow launchers (which use JCR events)

### Use Search Collections {#use-search-collections}

Different SRPs can have different native query languages. It is recommended to use methods from the [com.adobe.cq.social.ugc.api](/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/ugc/api/package-summary) package to invoke the appropriate query language.

For more information, see [Search Essentials](../../communities/using/search-implementation.md).

## Resources {#resources}

* [Community Content Storage](../../communities/using/working-with-srp.md) - discusses the available SRP choices for a UGC common store
* [Storage Resource Provider Overview](../../communities/using/srp.md) - introduction and repository usage overview
* [SRP and UGC Essentials](../../communities/using/srp-and-ugc.md) - SRP utility methods and examples
* [Search Essentials](../../communities/using/search-implementation.md) - essential information for searching UGC
* [SocialUtils Refactoring](../../communities/using/socialutils.md) - mapping deprecated utility methods to current SRP utility methods
