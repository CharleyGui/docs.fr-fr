---
title: 'Procédure : Charger et décharger des assemblys'
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: 77ea97c2fc324287e9c697d630def98241432c9f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973200"
---
# <a name="how-to-load-and-unload-assemblies"></a>Procédure : Charger et décharger des assemblys
Les assemblys référencés par votre programme sont automatiquement chargés par le common language runtime, mais il est également possible de charger dynamiquement des assemblys spécifiques dans le domaine d’application actuel. Pour plus d’informations, consultez [Guide pratique pour Charger des assemblys dans un domaine](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)d’application.

Dans .NET Framework, il n’existe aucun moyen de décharger un assembly individuel sans décharger tous les domaines d’application qui le contiennent. Même si l’assembly passe hors de portée, le fichier d’assembly proprement dit restera chargé jusqu’à ce que tous les domaines d’application qui le contiennent soient déchargés. Dans .net Core, la <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> classe gère le déchargement des assemblys. Pour plus d’informations, consultez [comment utiliser et déboguer l’inchargement d’assembly dans .net Core](unloadability.md).

## <a name="load-and-unload-assemblies"></a>Charger et décharger des assemblys

Pour charger un assembly dans un domaine d’application, utilisez l’une des nombreuses méthodes de chargement contenues <xref:System.Reflection.Assembly>dans les classes <xref:System.AppDomain> et. Pour plus d’informations, consultez [Guide pratique pour Charger des assemblys dans un domaine](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)d’application. Notez que .NET Core ne prend en charge qu’un seul domaine d’application. 

Pour décharger un assembly dans le .NET Framework, vous devez décharger tous les domaines d’application qui le contiennent. Pour décharger un domaine d’application <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> , utilisez la méthode. Pour plus d’informations, consultez [Guide pratique pour Décharger un](../../framework/app-domains/how-to-unload-an-application-domain.md)domaine d’application.

Si vous souhaitez décharger certains assemblys, mais pas d’autres dans une application .NET Framework, vous pouvez créer un nouveau domaine d’application, exécuter le code à l’intérieur de ce domaine, puis décharger ce domaine d’application. Pour plus d'informations, voir [Procédure : Décharger un](../../framework/app-domains/how-to-unload-an-application-domain.md)domaine d’application.  

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../../csharp/programming-guide/index.md)
- [Concepts de programmation (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Assemblys dans .NET](index.md)
- [Guide pratique pour Charger des assemblys dans un domaine d’application](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
