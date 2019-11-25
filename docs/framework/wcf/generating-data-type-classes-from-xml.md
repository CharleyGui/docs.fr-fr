---
title: Génération de classes de type de données à partir de XML
ms.date: 03/30/2017
ms.assetid: e4e5e4e8-527f-44d1-92fa-8904a08784ea
ms.openlocfilehash: 977b12b5c61c196a4f033361d37785e4ed0af73a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975854"
---
# <a name="generating-data-type-classes-from-xml"></a><span data-ttu-id="8ec14-102">Génération de classes de type de données à partir de XML</span><span class="sxs-lookup"><span data-stu-id="8ec14-102">Generating Data Type Classes from XML</span></span>
<span data-ttu-id="8ec14-103">.NET Framework 4,5 comprend une nouvelle fonctionnalité qui permet de générer des classes de type de données à partir de XML.</span><span class="sxs-lookup"><span data-stu-id="8ec14-103">.NET Framework 4.5 includes a new feature to generate data type classes from XML.</span></span> <span data-ttu-id="8ec14-104">Cette rubrique explique comment générer automatiquement des types de données pour le flux RSS du blog .NET.</span><span class="sxs-lookup"><span data-stu-id="8ec14-104">This topic describes how to automatically generate data types for the .NET Blog RSS feed.</span></span>  
  
### <a name="obtaining-the-xml-from-the-net-blog-rss-feed"></a><span data-ttu-id="8ec14-105">Obtention du XML à partir du flux RSS du blog .NET</span><span class="sxs-lookup"><span data-stu-id="8ec14-105">Obtaining the XML from the .NET Blog RSS feed</span></span>  
  
1. <span data-ttu-id="8ec14-106">Dans Internet Explorer, accédez au [flux RSS du blog .net](https://devblogs.microsoft.com/dotnet/feed/).</span><span class="sxs-lookup"><span data-stu-id="8ec14-106">In Internet Explorer, navigate to the [.NET Blog RSS feed](https://devblogs.microsoft.com/dotnet/feed/).</span></span>  
  
2. <span data-ttu-id="8ec14-107">Cliquez avec le bouton droit sur la page et sélectionnez **afficher la source**.</span><span class="sxs-lookup"><span data-stu-id="8ec14-107">Right-click the page and select **View Source**.</span></span>  
  
3. <span data-ttu-id="8ec14-108">Copiez le texte du flux en appuyant sur **Ctrl + A** pour sélectionner tout le texte, puis **Appuyez sur Ctrl + C** pour le copier.</span><span class="sxs-lookup"><span data-stu-id="8ec14-108">Copy the text of the feed by pressing **Ctrl+A** to select all text, and **Ctrl+C** to copy.</span></span>  
  
### <a name="creating-the-data-types"></a><span data-ttu-id="8ec14-109">Création des types de données</span><span class="sxs-lookup"><span data-stu-id="8ec14-109">Creating the data types</span></span>  
  
1. <span data-ttu-id="8ec14-110">Ouvrez un fichier de code où le proxy doit être utilisé.</span><span class="sxs-lookup"><span data-stu-id="8ec14-110">Open a code file where the proxy is to be used.</span></span> <span data-ttu-id="8ec14-111">Ce fichier doit faire partie d’un projet .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="8ec14-111">This file should be part of a .NET Framework 4.5 project.</span></span>  
  
2. <span data-ttu-id="8ec14-112">Placez le curseur dans un emplacement du fichier à l'extérieur des classes existantes.</span><span class="sxs-lookup"><span data-stu-id="8ec14-112">Place the cursor in a location in the file outside any existing classes.</span></span>  
  
3. <span data-ttu-id="8ec14-113">Sélectionnez **Edition**, **Collage spécial**, **coller XML en tant que classes**.</span><span class="sxs-lookup"><span data-stu-id="8ec14-113">Select **Edit**, **Paste Special**, **Paste XML as Classes**.</span></span>  
  
4. <span data-ttu-id="8ec14-114">Les classes appelées `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` et `rssChannelItemGuid` sont créées avec les membres nécessaires pour accéder aux éléments dans le flux RSS.</span><span class="sxs-lookup"><span data-stu-id="8ec14-114">Classes called `link`, `rss`, `rssChannel`, `rssChannelImage`, `rssChannelItem` and `rssChannelItemGuid` are created with the necessary members for accessing the elements in the RSS feed.</span></span>  
  
### <a name="using-the-generated-classes"></a><span data-ttu-id="8ec14-115">Utilisation des classes générées</span><span class="sxs-lookup"><span data-stu-id="8ec14-115">Using the generated classes</span></span>  
  
1. <span data-ttu-id="8ec14-116">Une fois les classes générées, elles peuvent être utilisées dans le code comme toute autre classe.</span><span class="sxs-lookup"><span data-stu-id="8ec14-116">Once the classes are generated, they can be used in code like any other classes.</span></span> <span data-ttu-id="8ec14-117">L'exemple suivant retourne une nouvelle instance de la classe `rssChannelImage`.</span><span class="sxs-lookup"><span data-stu-id="8ec14-117">The following code example returns a new instance of the `rssChannelImage` class.</span></span>  
  
    ```csharp
    var channelImage = new rssChannelImage()   
    {   
        title = "MyImage",   
        link = "http://www.contoso.com/images/channelImage.jpg",   
        url = "http://www.contoso.com/entries/myEntry.html"   
    };  
    ```
