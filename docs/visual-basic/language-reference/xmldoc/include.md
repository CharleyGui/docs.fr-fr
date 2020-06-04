---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 78a10624107cea349b01f484c641190a945dbd7e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400109"
---
# <a name="include-visual-basic"></a><span data-ttu-id="8d13b-101">\<include> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d13b-101">\<include> (Visual Basic)</span></span>
<span data-ttu-id="8d13b-102">Fait référence à un autre fichier qui décrit les types et les membres dans votre code source.</span><span class="sxs-lookup"><span data-stu-id="8d13b-102">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d13b-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d13b-103">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d13b-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8d13b-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="8d13b-105">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="8d13b-105">Required.</span></span> <span data-ttu-id="8d13b-106">Nom du fichier contenant la documentation.</span><span class="sxs-lookup"><span data-stu-id="8d13b-106">The name of the file containing the documentation.</span></span> <span data-ttu-id="8d13b-107">Le nom de fichier peut être qualifié avec un chemin.</span><span class="sxs-lookup"><span data-stu-id="8d13b-107">The file name can be qualified with a path.</span></span> <span data-ttu-id="8d13b-108">Mettez `filename` entre guillemets doubles ("").</span><span class="sxs-lookup"><span data-stu-id="8d13b-108">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="8d13b-109">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="8d13b-109">Required.</span></span> <span data-ttu-id="8d13b-110">Chemin des balises contenues dans `filename` qui mène à la balise `name`.</span><span class="sxs-lookup"><span data-stu-id="8d13b-110">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="8d13b-111">Placez le chemin d’accès entre guillemets doubles ("").</span><span class="sxs-lookup"><span data-stu-id="8d13b-111">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="8d13b-112">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="8d13b-112">Required.</span></span> <span data-ttu-id="8d13b-113">Spécificateur de nom dans la balise qui précède les commentaires.</span><span class="sxs-lookup"><span data-stu-id="8d13b-113">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="8d13b-114">`Name`aura un `id` .</span><span class="sxs-lookup"><span data-stu-id="8d13b-114">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="8d13b-115">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="8d13b-115">Required.</span></span> <span data-ttu-id="8d13b-116">ID de la balise qui précède les commentaires.</span><span class="sxs-lookup"><span data-stu-id="8d13b-116">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="8d13b-117">Mettez l’ID entre guillemets simples (' ').</span><span class="sxs-lookup"><span data-stu-id="8d13b-117">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d13b-118">Notes</span><span class="sxs-lookup"><span data-stu-id="8d13b-118">Remarks</span></span>  
 <span data-ttu-id="8d13b-119">Utilisez la `<include>` balise pour faire référence aux commentaires d’un autre fichier qui décrivent les types et les membres dans votre code source.</span><span class="sxs-lookup"><span data-stu-id="8d13b-119">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="8d13b-120">Il s’agit d’une solution alternative au placement direct des commentaires de la documentation dans votre fichier de code source.</span><span class="sxs-lookup"><span data-stu-id="8d13b-120">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="8d13b-121">La `<include>` balise utilise la recommandation W3C XML Path Language (XPath) Version 1,0.</span><span class="sxs-lookup"><span data-stu-id="8d13b-121">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="8d13b-122">Pour plus d’informations sur les méthodes de personnalisation de votre `<include>` utilisation, consultez <https://www.w3.org/TR/xpath> .</span><span class="sxs-lookup"><span data-stu-id="8d13b-122">For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d13b-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="8d13b-123">Example</span></span>  
 <span data-ttu-id="8d13b-124">Cet exemple utilise la `<include>` balise pour importer des commentaires de documentation de membre à partir d’un fichier appelé `commentFile.xml` .</span><span class="sxs-lookup"><span data-stu-id="8d13b-124">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 <span data-ttu-id="8d13b-125">Le format de `commentFile.xml` est le suivant.</span><span class="sxs-lookup"><span data-stu-id="8d13b-125">The format of the `commentFile.xml` is as follows.</span></span>  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d13b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d13b-126">See also</span></span>

- [<span data-ttu-id="8d13b-127">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="8d13b-127">XML Comment Tags</span></span>](index.md)
