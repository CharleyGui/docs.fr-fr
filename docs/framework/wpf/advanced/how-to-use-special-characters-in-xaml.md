---
title: Guide pratique pour utiliser des caractères spéciaux en XAML
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: 59449637bb45f6b75462b6809c354af7972fc2e7
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740831"
---
# <a name="how-to-use-special-characters-in-xaml"></a>Guide pratique pour utiliser des caractères spéciaux en XAML
Les fichiers de balisage créés dans Visual Studio sont enregistrés automatiquement au format de fichier Unicode UTF-8, ce qui signifie que la plupart des caractères spéciaux, tels que les marques d’accentuation, sont encodés correctement. Toutefois, il existe un ensemble de caractères spéciaux couramment utilisés qui sont gérés différemment. Ces caractères spéciaux suivent la norme XML du World Wide Web Consortium (W3C) pour l’encodage.  
  
 Le tableau suivant montre la syntaxe pour l’encodage de ce jeu de caractères spéciaux :  
  
|Caractère|Syntaxe|Description|  
|---------------|------------|-----------------|  
|<|`&lt;`|Signe Inférieur à.|  
|>|`&gt;`|Signe Supérieur à.|  
|&|`&amp;`|Symbole de Et commercial.|  
|"|`&quot;`|Symbole de guillemet double.|  
  
> [!NOTE]
> Si vous créez un fichier de balisage à l’aide d’un éditeur de texte, tel que le bloc-notes Windows, vous devez enregistrer le fichier au format de fichier Unicode UTF-8 afin de conserver tous les caractères spéciaux encodés.  
  
 L’exemple suivant montre comment utiliser des caractères spéciaux dans du texte lors de la création du balisage.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
