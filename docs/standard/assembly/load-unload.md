---
title: 'Comment : Charger et décharger les assemblages'
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: a520ffd41c3465737be7494d374cbcf64e3f1b85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155774"
---
# <a name="how-to-load-and-unload-assemblies"></a>Comment : Charger et décharger les assemblages
Les assemblages référencés par votre programme seront automatiquement chargés par l’heure d’exécution de la langue commune, mais il est également possible de charger dynamiquement des assemblages spécifiques dans le domaine d’application actuel. Pour plus d’informations, voir [Comment : Charger les assemblages dans un domaine d’application](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).

Dans .NET Framework, il n’y a aucun moyen de décharger un assemblage individuel sans décharger tous les domaines d’application qui le contiennent. Même si l’assembly passe hors de portée, le fichier d’assembly proprement dit restera chargé jusqu’à ce que tous les domaines d’application qui le contiennent soient déchargés. Dans .NET Core, la <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> classe gère le déchargement des assemblages. Pour plus d’informations, voir [Comment utiliser et débouger la déchargement de l’assemblage en .NET Core](unloadability.md).

## <a name="load-and-unload-assemblies"></a>Charger et décharger des assemblys

Pour charger un assemblage dans un domaine d’application, utilisez <xref:System.AppDomain> <xref:System.Reflection.Assembly>l’une des nombreuses méthodes de charge contenues dans les classes et . Pour plus d’informations, voir [Comment : Charger les assemblages dans un domaine d’application](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md). Notez que .NET Core ne prend en charge qu’un seul domaine d’application.

Pour décharger un assemblage dans le cadre .NET, vous devez décharger tous les domaines d’application qui le contiennent. Pour décharger un domaine <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> d’application, utilisez la méthode. Pour plus d’informations, voir [Comment : Décharger un domaine d’application](../../framework/app-domains/how-to-unload-an-application-domain.md).

Si vous souhaitez décharger certains assemblages mais pas d’autres dans une application cadre .NET, envisagez de créer un nouveau domaine d’application, d’exécuter le code à l’intérieur de ce domaine, puis de décharger ce domaine d’application. Pour plus d’informations, voir [Comment : Décharger un domaine d’application](../../framework/app-domains/how-to-unload-an-application-domain.md).  

## <a name="see-also"></a>Voir aussi

- [Guide de programmation CMD](../../csharp/programming-guide/index.md)
- [Concepts de programmation (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Assemblys dans .NET](index.md)
- [Comment : Charger les assemblages dans un domaine d’application](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
