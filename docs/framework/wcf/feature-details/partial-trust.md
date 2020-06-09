---
title: Confiance partielle
ms.date: 03/30/2017
ms.assetid: 489b1587-9909-4d0e-8c1a-5e83c8f8292b
ms.openlocfilehash: f4eace87593f2b4c45101bafa0843998a093cbd5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579148"
---
# <a name="partial-trust"></a><span data-ttu-id="45af4-102">Confiance partielle</span><span class="sxs-lookup"><span data-stu-id="45af4-102">Partial Trust</span></span>

<span data-ttu-id="45af4-103">À partir du .NET Framework 3,5, les appelants d’un niveau de confiance partiel peuvent accéder aux méthodes et types publics implémentés dans <xref:System.ServiceModel> , <xref:System.Runtime.Serialization> et <xref:System.ServiceModel.Web> .</span><span class="sxs-lookup"><span data-stu-id="45af4-103">Starting with the .NET Framework 3.5, partially trusted callers can access public types and methods implemented in <xref:System.ServiceModel>, <xref:System.Runtime.Serialization>, and <xref:System.ServiceModel.Web>.</span></span> <span data-ttu-id="45af4-104">Cette section décrit les scénarios pris en charge pour l’utilisation de Windows Communication Foundation (WCF) dans une application de confiance partielle, ainsi que le sous-ensemble limité de fonctionnalités WCF disponibles pour les applications qui s’exécutent avec des autorisations de sécurité d’accès du code réduites.</span><span class="sxs-lookup"><span data-stu-id="45af4-104">This section describes supported scenarios for using Windows Communication Foundation (WCF) within a partially trusted application as well as the limited subset of WCF functionality available to applications running with reduced code access security (CAS) permissions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45af4-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="45af4-105">In This Section</span></span>  
 [<span data-ttu-id="45af4-106">Supported Deployment Scenarios</span><span class="sxs-lookup"><span data-stu-id="45af4-106">Supported Deployment Scenarios</span></span>](supported-deployment-scenarios.md)  
 <span data-ttu-id="45af4-107">Décrit les principaux scénarios de confiance partielle pour l’exécution de WCF.</span><span class="sxs-lookup"><span data-stu-id="45af4-107">Describes the main partial trust scenarios for running WCF.</span></span>  
  
 [<span data-ttu-id="45af4-108">Compatibilité des fonctionnalités dans un environnement de confiance partielle</span><span class="sxs-lookup"><span data-stu-id="45af4-108">Partial Trust Feature Compatibility</span></span>](partial-trust-feature-compatibility.md)  
 <span data-ttu-id="45af4-109">Décrit les fonctionnalités WCF qui ne peuvent pas être utilisées avec une confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="45af4-109">Describes the WCF features that cannot be used with partial trust.</span></span>  
  
 [<span data-ttu-id="45af4-110">Partial Trust Best Practices</span><span class="sxs-lookup"><span data-stu-id="45af4-110">Partial Trust Best Practices</span></span>](partial-trust-best-practices.md)  
 <span data-ttu-id="45af4-111">Contient les meilleures pratiques pour l’utilisation de WCF dans des applications de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="45af4-111">Contains best practices for using WCF in partially trusted applications.</span></span>
