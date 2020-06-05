---
title: <para>
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: 0e2051d1b00b881c06082b3af483890d8595899f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400071"
---
# <a name="para-visual-basic"></a><span data-ttu-id="43d97-101">\<para> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43d97-101">\<para> (Visual Basic)</span></span>
<span data-ttu-id="43d97-102">Spécifie que le contenu est mis en forme en tant que paragraphe.</span><span class="sxs-lookup"><span data-stu-id="43d97-102">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43d97-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43d97-103">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
## <a name="parameters"></a><span data-ttu-id="43d97-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="43d97-104">Parameters</span></span>  
 `content`  
 <span data-ttu-id="43d97-105">Texte du paragraphe.</span><span class="sxs-lookup"><span data-stu-id="43d97-105">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43d97-106">Notes</span><span class="sxs-lookup"><span data-stu-id="43d97-106">Remarks</span></span>  
 <span data-ttu-id="43d97-107">La `<para>` balise est destinée à être utilisée à l’intérieur d’une balise, telle que [\<summary>](summary.md) , [\<remarks>](remarks.md) ou [\<returns>](returns.md) , et vous permet d’ajouter une structure au texte.</span><span class="sxs-lookup"><span data-stu-id="43d97-107">The `<para>` tag is for use inside a tag, such as [\<summary>](summary.md), [\<remarks>](remarks.md), or [\<returns>](returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="43d97-108">Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="43d97-108">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43d97-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="43d97-109">Example</span></span>  
 <span data-ttu-id="43d97-110">Cet exemple utilise la `<para>` balise pour fractionner la section Notes de la `UpdateRecord` méthode en deux paragraphes.</span><span class="sxs-lookup"><span data-stu-id="43d97-110">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="43d97-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43d97-111">See also</span></span>

- [<span data-ttu-id="43d97-112">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="43d97-112">XML Comment Tags</span></span>](index.md)
