---
title: Assemblys dans le Common Language Runtime
ms.date: 03/30/2017
helpviewer_keywords:
- dynamic assemblies
- security [.NET Framework], boundaries
- boundaries of assemblies
- assemblies [.NET Framework], about
- assemblies [.NET Framework], boundaries
- reference scope boundaries
- assemblies [.NET Framework]
- version boundaries
- type boundaries
ms.assetid: 2cfebe19-7436-49f1-bd99-3c4019f0b676
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3b516e43c07666f4b52e67f85cb567ab310f020
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832917"
---
# <a name="assemblies-in-the-common-language-runtime"></a>Assemblys dans le Common Language Runtime
Les assemblys sont les composantes des applications .NET Framework. Ils forment l’unité fondamentale de déploiement, de gestion de version, de réutilisation, de portée d’activation et des autorisations de sécurité. Un assembly est une collection de types et de ressources conçus pour opérer ensemble et former une unité logique de fonctionnalité. Un assembly fournit au Common Language Runtime les informations dont il a besoin pour connaître les implémentations de type. Pour le runtime, un type n'existe pas en dehors du contexte d'un assembly.  
  
 Un assembly remplit les fonctions suivantes :  
  
- Il contient le code que le Common Language Runtime exécute. Le code MSIL (Microsoft Intermediate Language) inclus dans un fichier exécutable portable (PE, portable executable) n'est pas exécuté s'il n'est pas associé à un manifeste d'assembly. Notez que chaque assembly ne peut comporter qu'un seul point d'entrée (c'est-à-dire `DllMain`, `WinMain` ou `Main`).  
  
- Il forme une frontière de sécurité. Un assembly est l'unité au niveau de laquelle les autorisations sont demandées et octroyées. Pour plus d’informations sur les limites de sécurité applicables aux assemblys, consultez [Aspects de la sécurité des assemblys](../../../docs/framework/app-domains/assembly-security-considerations.md).  
  
- Il constitue la limite d'un type. L'identité de chaque type inclut le nom de l'assembly dans lequel il réside. Un type appelé `MyType` chargé dans l'étendue d'un assembly n'est pas le même qu'un type appelé `MyType` chargé dans l'étendue d'un autre assembly.  
  
- Il constitue la limite de l'étendue de référence. Le manifeste de l'assembly contient des métadonnées d'assembly utilisées pour résoudre les types et satisfaire les demandes de ressources. Il spécifie les types et ressources exposés en dehors de l'assembly. Le manifeste énumère également les autres assemblys desquels il dépend.  
  
- Il forme une limite de version. L'assembly est l'unité avec version éventuelle la plus petite dans le Common Language Runtime. Tous les types et ressources inclus dans le même assembly se voient attribuer leur version dans le cadre d'une unité. Le manifeste de l'assembly décrit les dépendances de version que vous spécifiez pour les assemblys dépendants. Pour plus d’informations sur le contrôle de version, consultez [Contrôle de version des assemblys](../../../docs/framework/app-domains/assembly-versioning.md).  
  
- Il forme une unité de déploiement. Quand une application démarre, seuls les assemblys qu'elle appelle initialement doivent être présents. Les autres assemblys, comme les ressources de localisation ou les assemblys contenant des classes utilitaires, peuvent être récupérés à la demande. Ainsi, les applications restent simples et légères lors de leur premier téléchargement. Pour plus d’informations sur le déploiement des assemblys, consultez [Déploiement d’applications](../../../docs/framework/deployment/index.md).  
  
- Il forme l'unité au niveau de laquelle une exécution côte à côte est prise en charge. Pour plus d’informations sur l’exécution de plusieurs versions d’un assembly, consultez [Assemblys et exécution côte à côte](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md).  
  
 Les assemblys peuvent être statiques ou dynamiques. Les assemblys statiques peuvent inclure des types .NET Framework (interfaces et classes), ainsi que des ressources d'assembly (bitmaps, fichiers JPEG, fichiers de ressources, etc.). Les assemblys statiques sont stockés sur le disque dans des fichiers exécutables portables (PE). Vous pouvez également utiliser le .NET Framework pour créer des assemblys dynamiques, directement exécutés à partir de la mémoire et non enregistrés sur le disque avant leur exécution. Vous pouvez enregistrer des assemblys dynamiques sur le disque une fois qu'ils ont été exécutés.  
  
 Pour créer des assemblys, différentes possibilités s'offrent à vous. Vous pouvez utiliser les outils de développement, comme Visual Studio, que vous avez utilisés par le passé pour créer des fichiers .dll ou .exe. Vous pouvez utiliser les outils fournis dans le Kit de développement logiciel (SDK) Windows pour créer des assemblys avec des modules créés dans d'autres environnements de développement. Vous pouvez également utiliser les API du Common Language Runtime, comme <xref:System.Reflection.Emit?displayProperty=nameWithType>, pour créer des assemblys dynamiques.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Contenu d’un assembly](../../../docs/framework/app-domains/assembly-contents.md)|Décrit les éléments qui constituent un assembly.|  
|[Manifeste d’assembly](../../../docs/framework/app-domains/assembly-manifest.md)|Décrit les données incluses dans le manifeste d'assembly et la manière dont elles sont stockées dans les assemblys.|  
|[Global Assembly Cache](../../../docs/framework/app-domains/gac.md)|Décrit le Global Assembly Cache et la manière dont il est utilisé avec les assemblys.|  
|[Assemblys avec nom fort](../../../docs/framework/app-domains/strong-named-assemblies.md)|Décrit les caractéristiques des assemblys avec nom fort.|  
|[Aspects de la sécurité des assemblys](../../../docs/framework/app-domains/assembly-security-considerations.md)|Présente la manière dont la sécurité fonctionne avec les assemblys.|  
|[Contrôle de version des assemblys](../../../docs/framework/app-domains/assembly-versioning.md)|Fournit une vue d'ensemble de la stratégie de contrôle de version du .NET Framework.|  
|[Emplacement des assemblys](../../../docs/framework/app-domains/assembly-placement.md)|Explique où localiser les assemblys.|  
|[Assemblys et exécution côte à côte](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md)|Fournit une vue d'ensemble de l'utilisation simultanée de plusieurs versions du runtime ou d'un assembly.|  
|[Programmation à l’aide d’assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)|Décrit comment créer, signer et définir des attributs sur des assemblys.|  
|[Émission d’assemblys et de méthodes dynamiques](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Décrit comment créer des assemblys dynamiques.|  
|[Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|Décrit comment le .NET Framework résout les références d'assembly au moment de l'exécution.|  
  
## <a name="reference"></a>Référence  
 <xref:System.Reflection.Assembly?displayProperty=nameWithType>
