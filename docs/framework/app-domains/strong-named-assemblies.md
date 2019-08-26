---
title: Assemblys avec nom fort
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies, about strong-named assemblies
- assemblies [.NET Framework], strong-named
ms.assetid: d4a80263-f3e0-4d81-9b61-f0cbeae3797b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f283aad7c6727aff111aaaf78beb1e8da4b45898
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988367"
---
# <a name="strong-named-assemblies"></a>Assemblys avec nom fort
Attribuer un nom fort à un assembly permet de lui créer une identité unique pour prévenir d'éventuels conflits entre les assemblys.  
  
## <a name="what-makes-a-strong-named-assembly"></a>Qu'est-ce qu'un assembly avec nom fort ?  
 Un assembly avec nom fort est généré à l'aide de la clé privée qui correspond à la clé publique distribuée avec l'assembly et de l'assembly lui-même. L'assembly inclut le manifeste d'assembly, qui contient les noms et les hachages de tous les fichiers qui le composent. Les assemblys portant le même nom fort doivent être identiques.  
  
 Pour attribuer un nom fort à un assembly, vous pouvez utiliser Visual Studio ou un outil en ligne de commande. Pour plus d'informations, voir [Procédure : signer un assembly avec un nom fort](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md) ou [Sn.exe (outil Strong Name Tool)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).  
  
 Quand vous créez un assembly avec nom fort, il contient son nom de texte simple, son numéro de version, d'éventuelles informations sur sa culture, une signature numérique et la clé publique qui correspond à la clé privée utilisée pour la signature.  
  
> [!WARNING]
> Ne comptez pas sur les noms forts pour la sécurité. Ils fournissent seulement une identité unique.  
  
## <a name="why-strong-name-your-assemblies"></a>Pourquoi attribuer un nom fort à vos assemblys ?  
 Lorsque vous référencez un assembly avec nom fort, vous pouvez en attendre certains avantages, tels que la protection du contrôle de version et de l'affectation de nom. Dans certains scénarios, les assemblys avec nom fort doivent impérativement être installés dans le Global Assembly Cache.  
  
 Les assemblys avec nom fort s'avèrent utiles dans les scénarios suivants :  
  
- Vous voulez autoriser le référencement de vos assemblys par des assemblys avec nom fort ou vous souhaitez accorder un accès `friend` à vos assemblys à partir d'autres assemblys avec nom fort.  
  
- Une application a besoin d'accéder à différentes versions du même assembly. Les différentes versions d'un assembly doivent donc pouvoir se charger côte à côte dans le même domaine d'application sans générer de conflits. Par exemple, si différentes extensions d'une API existent dans des assemblys qui portent le même nom simple, l'attribution d'un nom fort fournit une identité unique à chaque version de l'assembly.  
  
- Vous souhaitez que votre assembly soit indépendant du domaine pour ne pas entraîner de baisse des performances des applications utilisant cet assembly. Comme un assembly indépendant du domaine doit être installé dans le Global Assembly Cache, cela nécessite d'attribuer des noms forts.  
  
- Vous voulez centraliser le traitement de votre application en appliquant une stratégie d'éditeur, ce qui implique d'installer l'assembly dans le Global Assembly Cache.  
  
 Si vous êtes développeur open source et que vous voulez bénéficier des avantages en matière d'identité d'un assembly avec nom fort, pensez à archiver la clé privée associée à l'assembly dans votre système de contrôle de code source.  
  
## <a name="see-also"></a>Voir aussi

- [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)
- [Guide pratique pour signer un assembly avec un nom fort](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)
- [Sn.exe (outil Strong Name)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [Création et utilisation d’assemblys avec nom fort](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
