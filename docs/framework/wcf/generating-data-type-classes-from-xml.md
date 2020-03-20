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
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="3fa59-102">Génération de classes de type de données à partir de XML</span><span class="sxs-lookup"><span data-stu-id="3fa59-102">Generating Data Type Classes from XML</span></span>
<span data-ttu-id="3fa59-103">.NET Framework 4.5 comprend une nouvelle fonctionnalité pour générer des classes de type de données à partir de XML.</span><span class="sxs-lookup"><span data-stu-id="3fa59-103">.NET Framework 4.5 includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="3fa59-104">Ce sujet décrit comment générer automatiquement des types de données pour le flux .NET Blog RSS.</span><span class="sxs-lookup"><span data-stu-id="3fa59-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="3fa59-105">Obtenir le XML à partir de la flux .NET Blog RSS</span><span class="sxs-lookup"><span data-stu-id="3fa59-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1. <span data-ttu-id="3fa59-106">Dans Internet Explorer, naviguez vers le [flux .NET Blog RSS](https://devblogs.microsoft.com/dotnet/feed/).</span><span class="sxs-lookup"><span data-stu-id="3fa59-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2. <span data-ttu-id="3fa59-107">Cliquez à droite sur la page et sélectionnez **View Source**.</span><span class="sxs-lookup"><span data-stu-id="3fa59-107">Right-click the page and select **View Source**.</span></span>  
  
3. <span data-ttu-id="3fa59-108">Copiez le texte du flux en appuyant sur **Ctrl-A** pour sélectionner tous les textes et **Ctrl-C** à copier.</span><span class="sxs-lookup"><span data-stu-id="3fa59-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="3fa59-109">Création des types de données</span><span class="sxs-lookup"><span data-stu-id="3fa59-109">Creating the data types</span></span>  
  
1. <span data-ttu-id="3fa59-110">Ouvrez un fichier de code où le proxy doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="3fa59-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="3fa59-111">Ce fichier devrait faire partie d’un projet .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="3fa59-111">This file should be part of a .NET Framework 4.5 project.</span></span>  
  
2. <span data-ttu-id="3fa59-112">Placez le curseur dans un emplacement du fichier à l'extérieur des classes existantes.</span><span class="sxs-lookup"><span data-stu-id="3fa59-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3. <span data-ttu-id="3fa59-113">Sélectionnez **Edit**, **Coller Spécial**, **Pâte XML comme Classes**.</span><span class="sxs-lookup"><span data-stu-id="3fa59-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4. <span data-ttu-id="3fa59-114">Classes `link`appelées `rssChannel` `rssChannelImage`, `rssChannelItem` `rss` `rssChannelItemGuid` , , et sont créés avec les membres nécessaires pour accéder aux éléments dans le flux RSS.</span><span class="sxs-lookup"><span data-stu-id="3fa59-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="3fa59-115">Utilisation des classes générées</span><span class="sxs-lookup"><span data-stu-id="3fa59-115">Using the generated classes</span></span>  
  
1. <span data-ttu-id="3fa59-116">Une fois les classes générées, elles peuvent être utilisées dans le code comme toute autre classe.</span><span class="sxs-lookup"><span data-stu-id="3fa59-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="3fa59-117">L'exemple suivant retourne une nouvelle instance de la classe `rssChannelImage`.</span><span class="sxs-lookup"><span data-stu-id="3fa59-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```csharp
    var channelImage = new rssChannelImage()
    {
        title = "MyImage",
        link = "http://www.contoso.com/images/channelImage.jpg",
        url = "http://www.contoso.com/entries/myEntry.html"
    };  
    ```
