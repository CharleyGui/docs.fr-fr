---
title: <list>
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: db5c571d2f2c59419c886f6596f4e4dbd30d7baf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352322"
---
# <a name="list-visual-basic"></a><span data-ttu-id="3f30e-101">> de la liste de \<(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f30e-101">\<list> (Visual Basic)</span></span>
<span data-ttu-id="3f30e-102">Définit une liste ou une table.</span><span class="sxs-lookup"><span data-stu-id="3f30e-102">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f30e-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f30e-103">Syntax</span></span>  
  
```xml  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f30e-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3f30e-104">Parameters</span></span>  
 `type`  
 <span data-ttu-id="3f30e-105">Type de la liste.</span><span class="sxs-lookup"><span data-stu-id="3f30e-105">The type of the list.</span></span> <span data-ttu-id="3f30e-106">Doit être une « puce » pour une liste à puces, « nombre » pour une liste numérotée ou « table » pour une table à deux colonnes.</span><span class="sxs-lookup"><span data-stu-id="3f30e-106">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="3f30e-107">Utilisé uniquement lorsque `type` est « table ».</span><span class="sxs-lookup"><span data-stu-id="3f30e-107">Only used when `type` is "table."</span></span> <span data-ttu-id="3f30e-108">Terme à définir, qui est défini dans la balise de description.</span><span class="sxs-lookup"><span data-stu-id="3f30e-108">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="3f30e-109">Lorsque `type` est « Bullet » ou « Number », `description` est un élément de la liste lorsque `type` est « table », `description` est la définition de `term`.</span><span class="sxs-lookup"><span data-stu-id="3f30e-109">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f30e-110">Notes</span><span class="sxs-lookup"><span data-stu-id="3f30e-110">Remarks</span></span>  
 <span data-ttu-id="3f30e-111">Le bloc `<listheader>` définit le titre d’une table ou d’une liste de définitions.</span><span class="sxs-lookup"><span data-stu-id="3f30e-111">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="3f30e-112">Lors de la définition d’une table, il vous suffit de fournir une entrée pour `term` dans l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="3f30e-112">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="3f30e-113">Chaque élément de la liste est spécifié avec un bloc `<item>`.</span><span class="sxs-lookup"><span data-stu-id="3f30e-113">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="3f30e-114">Lorsque vous créez une liste de définitions, vous devez spécifier à la fois `term` et `description`.</span><span class="sxs-lookup"><span data-stu-id="3f30e-114">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="3f30e-115">Toutefois, pour une table, une liste à puces ou une liste numérotée, il vous suffit de fournir une entrée pour `description`.</span><span class="sxs-lookup"><span data-stu-id="3f30e-115">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="3f30e-116">Une liste ou une table peut avoir autant de blocs `<item>` que nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3f30e-116">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="3f30e-117">Compilez avec [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="3f30e-117">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f30e-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f30e-118">Example</span></span>  
 <span data-ttu-id="3f30e-119">Cet exemple utilise la balise `<list>` pour définir une liste à puces dans la section Notes.</span><span class="sxs-lookup"><span data-stu-id="3f30e-119">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="3f30e-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f30e-120">See also</span></span>

- [<span data-ttu-id="3f30e-121">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="3f30e-121">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
