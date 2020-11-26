---
title: Génération de classes de type de données à partir de XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: a7920a8c8c4f279dd3fc52029c5da5e9b685efe2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238247"
---
# <a name="generating-data-type-classes-from-xml"></a>Génération de classes de type de données à partir de XML

.NET Framework 4,5 comprend une nouvelle fonctionnalité qui permet de générer des classes de type de données à partir de XML. Cette rubrique explique comment générer automatiquement des types de données pour le flux RSS du blog .NET.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>Obtention du XML à partir du flux RSS du blog .NET  
  
1. Dans Internet Explorer, accédez au [flux RSS du blog .net](https://devblogs.microsoft.com/dotnet/feed/).  
  
2. Cliquez avec le bouton droit sur la page et sélectionnez **afficher la source**.  
  
3. Copiez le texte du flux en appuyant sur **Ctrl + A** pour sélectionner tout le texte, puis **Appuyez sur Ctrl + C** pour le copier.  
  
### <a name="creating-the-data-types"></a>Création des types de données  
  
1. Ouvrez un fichier de code où le proxy doit être utilisé. Ce fichier doit faire partie d’un projet .NET Framework 4,5.  
  
2. Placez le curseur dans un emplacement du fichier à l'extérieur des classes existantes.  
  
3. Sélectionnez **Edition**, **Collage spécial**, **coller XML en tant que classes**.  
  
4. Les classes appelées `link` , `rss` , `rssChannel` , `rssChannelImage` `rssChannelItem` et `rssChannelItemGuid` sont créées avec les membres nécessaires pour accéder aux éléments dans le flux RSS.  
  
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
