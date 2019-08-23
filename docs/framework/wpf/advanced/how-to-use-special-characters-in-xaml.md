---
title: 'Procédure : Utiliser des caractères spéciaux en XAML'
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: 61ee38319b2f0aa46690fb063f6ffe6612f993ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918438"
---
# <a name="how-to-use-special-characters-in-xaml"></a>Procédure : Utiliser des caractères spéciaux en XAML
Les fichiers de balisage créés [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] dans sont enregistrés automatiquement [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] au format de fichier UTF-8, ce qui signifie que la plupart des caractères spéciaux, tels que les accents, sont encodés correctement. Toutefois, il existe un ensemble de caractères spéciaux couramment utilisés qui sont gérés différemment. Ces caractères spéciaux sont conformes [!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] à la [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] norme de codage.  
  
 Le tableau suivant montre la syntaxe pour l’encodage de ce jeu de caractères spéciaux :  
  
|Caractère|Syntaxe|Description|  
|---------------|------------|-----------------|  
|<|`&lt;`|Signe Inférieur à.|  
|>|`&gt;`|Signe Supérieur à.|  
|&|`&amp;`|Symbole de Et commercial.|  
|"|`&quot;`|Symbole de guillemet double.|  
  
> [!NOTE]
> Si vous créez un fichier de balisage à l’aide d’un éditeur de texte, tel que le bloc-notes [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] Windows, vous devez enregistrer le fichier au format de fichier UTF-8 afin de conserver tous les caractères spéciaux encodés.  
  
 L’exemple suivant montre comment utiliser des caractères spéciaux dans du texte lors de la création du balisage.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
