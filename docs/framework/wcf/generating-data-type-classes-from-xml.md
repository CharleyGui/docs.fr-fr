---
title: Génération de classes de type de données à partir de XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: d66cbd1806b90d21a483d0c470f953ddfb9c4fca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184133"
---
# <a name="generating-data-type-classes-from-xml"></a>Génération de classes de type de données à partir de XML
.NET Framework 4.5 comprend une nouvelle fonctionnalité pour générer des classes de type de données à partir de XML. Ce sujet décrit comment générer automatiquement des types de données pour le flux .NET Blog RSS.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>Obtenir le XML à partir de la flux .NET Blog RSS  
  
1. Dans Internet Explorer, naviguez vers le [flux .NET Blog RSS](https://devblogs.microsoft.com/dotnet/feed/).  
  
2. Cliquez à droite sur la page et sélectionnez **View Source**.  
  
3. Copiez le texte du flux en appuyant sur **Ctrl-A** pour sélectionner tous les textes et **Ctrl-C** à copier.  
  
### <a name="creating-the-data-types"></a>Création des types de données  
  
1. Ouvrez un fichier de code où le proxy doit être utilisé. Ce fichier devrait faire partie d’un projet .NET Framework 4.5.  
  
2. Placez le curseur dans un emplacement du fichier à l'extérieur des classes existantes.  
  
3. Sélectionnez **Edit**, **Coller Spécial**, **Pâte XML comme Classes**.  
  
4. Classes `link`appelées `rssChannel` `rssChannelImage`, `rssChannelItem` `rss` `rssChannelItemGuid` , , et sont créés avec les membres nécessaires pour accéder aux éléments dans le flux RSS.  
  
### <a name="using-the-generated-classes"></a>Utilisation des classes générées  
  
1. Une fois les classes générées, elles peuvent être utilisées dans le code comme toute autre classe. L'exemple suivant retourne une nouvelle instance de la classe `rssChannelImage`.  
  
    ```csharp
    var channelImage = new rssChannelImage()
    {
        title = "MyImage",
        link = "http://www.contoso.com/images/channelImage.jpg",
        url = "http://www.contoso.com/entries/myEntry.html"
    };  
    ```
