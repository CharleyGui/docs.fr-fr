---
title: Assemblys avec nom fort
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, about strong-named assemblies
- assemblies [.NET Framework], strong-named
ms.assetid: d4a80263-f3e0-4d81-9b61-f0cbeae3797b
ms.openlocfilehash: 12b8df3195b2708e4556d4f8065227054db9eb14
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711569"
---
# <a name="strong-named-assemblies"></a>Assemblys avec nom fort

Attribuer un nom fort à un assembly permet de lui créer une identité unique pour prévenir d'éventuels conflits entre les assemblys.

## <a name="what-makes-a-strong-named-assembly"></a>Qu'est-ce qu'un assembly avec nom fort ?

Un assembly avec nom fort est généré à l'aide de la clé privée qui correspond à la clé publique distribuée avec l'assembly et de l'assembly lui-même. L'assembly inclut le manifeste d'assembly, qui contient les noms et les hachages de tous les fichiers qui le composent. Les assemblys portant le même nom fort doivent être identiques.

Pour attribuer un nom fort à un assembly, vous pouvez utiliser Visual Studio ou un outil en ligne de commande. Pour plus d’informations, voir [Comment : Signez un assemblage avec un nom fort](sign-strong-name.md) ou [Sn.exe (outil Strong Name)](../../framework/tools/sn-exe-strong-name-tool.md).

Quand vous créez un assembly avec nom fort, il contient son nom de texte simple, son numéro de version, d'éventuelles informations sur sa culture, une signature numérique et la clé publique qui correspond à la clé privée utilisée pour la signature.

> [!WARNING]
> Ne comptez pas sur les noms forts pour la sécurité. Ils fournissent seulement une identité unique.

## <a name="why-strong-name-your-assemblies"></a>Pourquoi attribuer un nom fort à vos assemblys ?

Lorsque vous référencez un assembly avec nom fort, vous pouvez en attendre certains avantages, tels que la protection du contrôle de version et de l'affectation de nom. Dans le cadre .NET, des assemblages nommés par des points forts peuvent être installés dans le cache d’assemblage global, qui est nécessaire pour activer certains scénarios.

Les assemblys avec nom fort s'avèrent utiles dans les scénarios suivants :

- Vous voulez autoriser le référencement de vos assemblys par des assemblys avec nom fort ou vous souhaitez accorder un accès `friend` à vos assemblys à partir d'autres assemblys avec nom fort.

- Une application a besoin d'accéder à différentes versions du même assembly. Les différentes versions d'un assembly doivent donc pouvoir se charger côte à côte dans le même domaine d'application sans générer de conflits. Par exemple, si différentes extensions d'une API existent dans des assemblys qui portent le même nom simple, l'attribution d'un nom fort fournit une identité unique à chaque version de l'assembly.

- Vous souhaitez que votre assembly soit indépendant du domaine pour ne pas entraîner de baisse des performances des applications utilisant cet assembly. Comme un assembly indépendant du domaine doit être installé dans le Global Assembly Cache, cela nécessite d'attribuer des noms forts.

- Vous souhaitez centraliser l’entretien de votre application en appliquant la politique de l’éditeur, ce qui signifie que l’assemblage doit être installé dans le cache d’assemblage global.

Si vous êtes un développeur open-source et que vous voulez les avantages d’identité d’un assemblage fort, envisagez de vérifier la clé privée associée à un assemblage à votre système de contrôle source.

## <a name="see-also"></a>Voir aussi

- [Cache d’assemblage global](../../framework/app-domains/gac.md)
- [Comment: Signer une assemblée avec un nom fort](sign-strong-name.md)
- [Sn.exe (outil Strong Name)](../../framework/tools/sn-exe-strong-name-tool.md)
- [Créer et utiliser des assemblys avec nom fort](create-use-strong-named.md)
