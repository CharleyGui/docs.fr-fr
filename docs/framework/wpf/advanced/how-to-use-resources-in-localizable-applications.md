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
# <a name="how-to-use-resources-in-localizable-apps"></a>Comment : utiliser des ressources dans des applications localisables

La localisation consiste à adapter une interface utilisateur à différentes cultures. Pour ce faire, du texte tel que des titres, des légendes et des éléments de zone de liste doit être traduit. Pour faciliter la traduction, les éléments à traduire sont collectés dans des fichiers de ressources. Pour plus d’informations sur la création d’un fichier de ressources pour la localisation, consultez [localiser une application](how-to-localize-an-application.md) . Pour rendre une application WPF localisable, les développeurs doivent générer toutes les ressources localisables dans un assembly de ressources. L’assembly de ressource est localisé dans différentes langues et le code-behind utilise l’API de gestion des ressources pour le chargement.

## <a name="example"></a>Exemple

L’un des fichiers requis pour une application WPF est un fichier projet (. proj). Toutes les ressources que vous utilisez dans votre application doivent être comprises dans le fichier projet. L’exemple de code XAML suivant illustre cela.

```xaml
<Resource Include="data\picture1.jpg"/>  
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

Pour utiliser une ressource dans votre application, instanciez <xref:System.Resources.ResourceManager> et chargez la ressource que vous souhaitez utiliser. Le code C# suivant montre comment procéder.

[!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

## <a name="see-also"></a>Voir aussi

- [Localiser une application](how-to-localize-an-application.md)
