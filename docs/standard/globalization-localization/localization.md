---
title: Localisation
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, localization
- application development [.NET], localization
- globalization [.NET], localization
- code blocks
- international applications [.NET], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
ms.openlocfilehash: e92184f48b2d2255138da5b2a6e7e2977a95e2e3
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93062956"
---
# <a name="localization"></a>Localisation

La localisation correspond au processus de traduction des ressources d’une application dans des versions localisées pour chaque culture prise en charge par l’application. Vous devez passer à l’étape de localisation uniquement après avoir effectué l’étape [Révision de l’adaptabilité](localizability-review.md) pour vérifier que l’application globalisée est prête pour la localisation.

Une application prête pour la localisation est divisée en deux blocs conceptuels, un bloc qui contient tous les éléments d’interface utilisateur et un bloc qui contient le code exécutable. Le bloc d’interface utilisateur contient uniquement les éléments d’interface utilisateur localisables, comme les chaînes, les messages d’erreur, les boîtes de dialogue, les menus, les ressources d’objet incorporées, etc. relatifs à la culture neutre. Le bloc de code contient uniquement le code d’application à utiliser par toutes les cultures prises en charge. Le CLR prend en charge un modèle de ressource d’assembly satellite qui sépare le code exécutable d’une application de ses ressources. Pour plus d’informations sur l’implémentation de ce modèle, consultez [Ressources dans .NET](../../framework/resources/index.md).

Pour chaque version localisée de votre application, ajoutez un nouvel assembly satellite contenant le bloc d’interface utilisateur localisée traduit dans la langue appropriée pour la culture cible. Le bloc de code pour toutes les cultures doit rester le même. La combinaison d’une version localisée du bloc d’interface utilisateur et du bloc de code produit une version localisée de votre application.

Le SDK Windows fournit le Windows Forms Resource Editor (Winres.exe), qui vous permet de localiser rapidement des Windows Forms pour les cultures cibles. Pour plus d’informations sur l’utilisation de cet outil, consultez [Winres.exe (Windows Forms Resource Editor)](../../framework/tools/winres-exe-windows-forms-resource-editor.md).

## <a name="see-also"></a>Voir aussi

- [Globalisation et localisation](index.md)
- [Revue de l’adaptabilité](localizability-review.md)
- [Globalisation](globalization.md)
- [Ressources dans les applications de bureau](../../framework/resources/index.md)
