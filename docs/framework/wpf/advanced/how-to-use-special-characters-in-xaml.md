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
ms.openlocfilehash: 27f2b18593d075b54eb8c3351bbb84415700cfd4
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395805"
---
# <a name="how-to-use-special-characters-in-xaml"></a>Guide pratique pour utiliser des caractères spéciaux en XAML
Les fichiers de balisage créés dans [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] sont enregistrés automatiquement au format de fichier Unicode UTF-8, ce qui signifie que la plupart des caractères spéciaux, tels que les accents, sont encodés correctement. Toutefois, il existe un ensemble de caractères spéciaux couramment utilisés qui sont gérés différemment. Ces caractères spéciaux suivent la norme [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] pour l’encodage.  
  
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
