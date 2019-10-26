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
ms.openlocfilehash: 713428adc2e1576d1b95984b492fe84c042c0a09
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919644"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="80168-102">Guide pratique pour utiliser des caractères spéciaux en XAML</span><span class="sxs-lookup"><span data-stu-id="80168-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="80168-103">Les fichiers de balisage créés dans Visual Studio sont enregistrés automatiquement au format de fichier Unicode UTF-8, ce qui signifie que la plupart des caractères spéciaux, tels que les marques d’accentuation, sont encodés correctement.</span><span class="sxs-lookup"><span data-stu-id="80168-103">Markup files that are created in Visual Studio are automatically saved in the Unicode UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="80168-104">Toutefois, il existe un ensemble de caractères spéciaux couramment utilisés qui sont gérés différemment.</span><span class="sxs-lookup"><span data-stu-id="80168-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="80168-105">Ces caractères spéciaux sont conformes aux World Wide Web Consortium (W3C) [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard pour l’encodage.</span><span class="sxs-lookup"><span data-stu-id="80168-105">These special characters follow the World Wide Web Consortium (W3C) [!INCLUDE[TL A#tla_xml](../../../../includes/tlasharptla-xml-md.md)] standard for encoding.</span></span>  
  
 <span data-ttu-id="80168-106">Le tableau suivant montre la syntaxe pour l’encodage de ce jeu de caractères spéciaux :</span><span class="sxs-lookup"><span data-stu-id="80168-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="80168-107">Caractère</span><span class="sxs-lookup"><span data-stu-id="80168-107">Character</span></span>|<span data-ttu-id="80168-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80168-108">Syntax</span></span>|<span data-ttu-id="80168-109">Description</span><span class="sxs-lookup"><span data-stu-id="80168-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="80168-110">Signe Inférieur à.</span><span class="sxs-lookup"><span data-stu-id="80168-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="80168-111">Signe Supérieur à.</span><span class="sxs-lookup"><span data-stu-id="80168-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="80168-112">Symbole de Et commercial.</span><span class="sxs-lookup"><span data-stu-id="80168-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="80168-113">"</span><span class="sxs-lookup"><span data-stu-id="80168-113">"</span></span>|`&quot;`|<span data-ttu-id="80168-114">Symbole de guillemet double.</span><span class="sxs-lookup"><span data-stu-id="80168-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="80168-115">Si vous créez un fichier de balisage à l’aide d’un éditeur de texte, tel que le bloc-notes Windows, vous devez enregistrer le fichier au format de fichier Unicode UTF-8 afin de conserver tous les caractères spéciaux encodés.</span><span class="sxs-lookup"><span data-stu-id="80168-115">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the Unicode UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="80168-116">L’exemple suivant montre comment utiliser des caractères spéciaux dans du texte lors de la création du balisage.</span><span class="sxs-lookup"><span data-stu-id="80168-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80168-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="80168-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
