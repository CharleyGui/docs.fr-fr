---
title: Génération de classes de type de données à partir de XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: b99bb40105398dbd91b910c4a19828d069c3d9e7
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380219"
---
# <a name="generating-data-type-classes-from-xml"></a>Génération de classes de type de données à partir de XML
.NET framework 4.5 inclut une nouvelle fonctionnalité pour générer des classes de type de données à partir de XML. Cette rubrique décrit comment générer automatiquement des types de données pour les flux RSS du Blog .NET.  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a>Obtention du code XML à partir du RSS du Blog .NET de flux  
  
1. Dans Internet Explorer, accédez à la [RSS du Blog .NET flux](https://devblogs.microsoft.com/dotnet/feed/).  
  
2. Cliquez sur la page et sélectionnez **afficher la Source**.  
  
3. Copiez le texte du flux en appuyant sur **Ctrl + A** pour sélectionner tout le texte, et **Ctrl + C** à copier.  
  
### <a name="creating-the-data-types"></a>Création des types de données  
  
1. Ouvrez un fichier de code où le proxy doit être utilisé. Ce fichier doit faire partie d’un projet .NET Framework 4.5.  
  
2. Placez le curseur dans un emplacement du fichier à l'extérieur des classes existantes.  
  
3. Sélectionnez **modifier**, **Collage spécial**, **coller XML en tant que Classes**.  
  
4. Classes appelées `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` et `rssChannelItemGuid` sont créés avec les membres nécessaires pour accéder aux éléments dans le flux RSS.  
  
### <a name="using-the-generated-classes"></a>Utilisation des classes générées  
  
1. Une fois les classes générées, elles peuvent être utilisées dans le code comme toute autre classe. L'exemple suivant retourne une nouvelle instance de la classe `rssChannelImage`.  
  
    ```  
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
