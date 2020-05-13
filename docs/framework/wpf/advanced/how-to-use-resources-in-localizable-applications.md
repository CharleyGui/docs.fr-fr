---
title: Guide pratique pour utiliser des ressources dans des applications localisables
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: 8f516a86036656b98add23d38c588b5c19be4d7a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212473"
---
# <a name="how-to-use-resources-in-localizable-apps"></a><span data-ttu-id="a3145-102">Comment : utiliser des ressources dans des applications localisables</span><span class="sxs-lookup"><span data-stu-id="a3145-102">How to: Use resources in localizable apps</span></span>

<span data-ttu-id="a3145-103">La localisation consiste à adapter une interface utilisateur à différentes cultures.</span><span class="sxs-lookup"><span data-stu-id="a3145-103">Localization means to adapt a user interface to different cultures.</span></span> <span data-ttu-id="a3145-104">Pour ce faire, du texte tel que des titres, des légendes et des éléments de zone de liste doit être traduit.</span><span class="sxs-lookup"><span data-stu-id="a3145-104">To do this, text such as titles, captions, and list box items must be translated.</span></span> <span data-ttu-id="a3145-105">Pour faciliter la traduction, les éléments à traduire sont collectés dans des fichiers de ressources.</span><span class="sxs-lookup"><span data-stu-id="a3145-105">To make translation easier, the items to be translated are collected into resource files.</span></span> <span data-ttu-id="a3145-106">Pour plus d’informations sur la création d’un fichier de ressources pour la localisation, consultez [localiser une application](how-to-localize-an-application.md) .</span><span class="sxs-lookup"><span data-stu-id="a3145-106">See [Localize an app](how-to-localize-an-application.md) for information on how to create a resource file for localization.</span></span> <span data-ttu-id="a3145-107">Pour rendre une application WPF localisable, les développeurs doivent générer toutes les ressources localisables dans un assembly de ressources.</span><span class="sxs-lookup"><span data-stu-id="a3145-107">To make a WPF application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="a3145-108">L’assembly de ressource est localisé dans différentes langues et le code-behind utilise l’API de gestion des ressources pour le chargement.</span><span class="sxs-lookup"><span data-stu-id="a3145-108">The resource assembly is localized into different languages, and the code-behind uses resource management API to load.</span></span>

## <a name="example"></a><span data-ttu-id="a3145-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="a3145-109">Example</span></span>

<span data-ttu-id="a3145-110">L’un des fichiers requis pour une application WPF est un fichier projet (. proj).</span><span class="sxs-lookup"><span data-stu-id="a3145-110">One of the files required for a WPF application is a project file (.proj).</span></span> <span data-ttu-id="a3145-111">Toutes les ressources que vous utilisez dans votre application doivent être comprises dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="a3145-111">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="a3145-112">L’exemple de code XAML suivant illustre cela.</span><span class="sxs-lookup"><span data-stu-id="a3145-112">The following XAML example shows this.</span></span>

```xaml
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

<span data-ttu-id="a3145-113">Pour utiliser une ressource dans votre application, instanciez <xref:System.Resources.ResourceManager> et chargez la ressource que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="a3145-113">To use a resource in your application, instantiate <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="a3145-114">Le code C# suivant montre comment procéder.</span><span class="sxs-lookup"><span data-stu-id="a3145-114">The following C# code demonstrates how to do this.</span></span>

[!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

## <a name="see-also"></a><span data-ttu-id="a3145-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3145-115">See also</span></span>

- [<span data-ttu-id="a3145-116">Localiser une application</span><span class="sxs-lookup"><span data-stu-id="a3145-116">Localize an app</span></span>](how-to-localize-an-application.md)
