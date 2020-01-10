---
title: <include> - Guide de programmation C#
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: 125ab9476507babae9a707a6c42d24adda632267
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75696556"
---
# <a name="include-c-programming-guide"></a><span data-ttu-id="e24da-102">\<include> (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e24da-102">\<include> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="e24da-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e24da-103">Syntax</span></span>  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
## <a name="parameters"></a><span data-ttu-id="e24da-104">Parameters</span><span class="sxs-lookup"><span data-stu-id="e24da-104">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="e24da-105">Nom du fichier XML contenant la documentation.</span><span class="sxs-lookup"><span data-stu-id="e24da-105">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="e24da-106">Le nom de fichier peut être qualifié avec un chemin relatif au fichier de code source.</span><span class="sxs-lookup"><span data-stu-id="e24da-106">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="e24da-107">Mettez `filename` entre guillemets simples (' ').</span><span class="sxs-lookup"><span data-stu-id="e24da-107">Enclose `filename` in single quotation marks (' ').</span></span>  
  
 `tagpath`  
 <span data-ttu-id="e24da-108">Chemin des balises contenues dans `filename` qui mène à la balise `name`.</span><span class="sxs-lookup"><span data-stu-id="e24da-108">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="e24da-109">Mettez le chemin entre guillemets simples (' ').</span><span class="sxs-lookup"><span data-stu-id="e24da-109">Enclose the path in single quotation marks (' ').</span></span>  
  
 `name`  
 <span data-ttu-id="e24da-110">Spécificateur de nom contenu dans la balise qui précède les commentaires ; `name` possède un `id`.</span><span class="sxs-lookup"><span data-stu-id="e24da-110">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="e24da-111">ID de la balise qui précède les commentaires.</span><span class="sxs-lookup"><span data-stu-id="e24da-111">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="e24da-112">Mettez l’ID entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="e24da-112">Enclose the ID in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e24da-113">Notes</span><span class="sxs-lookup"><span data-stu-id="e24da-113">Remarks</span></span>  
 <span data-ttu-id="e24da-114">La balise \<include> vous permet de faire référence à des commentaires dans un autre fichier qui décrivent les types et les membres dans votre code source.</span><span class="sxs-lookup"><span data-stu-id="e24da-114">The \<include> tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="e24da-115">Il s’agit d’une solution alternative au placement direct des commentaires de la documentation dans votre fichier de code source.</span><span class="sxs-lookup"><span data-stu-id="e24da-115">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="e24da-116">En plaçant la documentation dans un fichier distinct, vous pouvez appliquer un contrôle de code source à la documentation indépendamment du code source.</span><span class="sxs-lookup"><span data-stu-id="e24da-116">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="e24da-117">Ainsi, une personne peut extraire le fichier de code source et une autre personne peut extraire le fichier de documentation.</span><span class="sxs-lookup"><span data-stu-id="e24da-117">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>  
  
 <span data-ttu-id="e24da-118">La balise \<include> utilise la syntaxe XML XPath.</span><span class="sxs-lookup"><span data-stu-id="e24da-118">The \<include> tag uses the XML XPath syntax.</span></span> <span data-ttu-id="e24da-119">Reportez-vous à la documentation de XPath pour savoir comment personnaliser votre utilisation de \<include>.</span><span class="sxs-lookup"><span data-stu-id="e24da-119">Refer to XPath documentation for ways to customize your \<include> use.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e24da-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="e24da-120">Example</span></span>  
 <span data-ttu-id="e24da-121">Cet exemple comprend plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="e24da-121">This is a multifile example.</span></span> <span data-ttu-id="e24da-122">Le premier, qui utilise \<include>, est présenté ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="e24da-122">The first file, which uses \<include>, is listed below:</span></span>  
  
 [!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]  
  
 <span data-ttu-id="e24da-123">Le deuxième, xml_include_tag.doc, contient les commentaires de la documentation suivants :</span><span class="sxs-lookup"><span data-stu-id="e24da-123">The second file, xml_include_tag.doc, contains the following documentation comments:</span></span>  
  
```xml  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## <a name="program-output"></a><span data-ttu-id="e24da-124">Sortie du programme</span><span class="sxs-lookup"><span data-stu-id="e24da-124">Program Output</span></span>  
 <span data-ttu-id="e24da-125">La sortie suivante est générée quand vous compilez les classes Test et Test2 avec la ligne de commande suivante : `/doc:DocFileName.xml.` Dans Visual Studio, l’option de commentaires de document XML est spécifiée dans le volet de génération du Concepteur de projet.</span><span class="sxs-lookup"><span data-stu-id="e24da-125">The following output is generated when you compile the Test and Test2 classes with the following command line: `/doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="e24da-126">Dès que le compilateur C# trouve la balise \<include>, il recherche des commentaires de la documentation dans xml_include_tag.doc et non dans le fichier source actuel.</span><span class="sxs-lookup"><span data-stu-id="e24da-126">When the C# compiler sees the \<include> tag, it will search for documentation comments in xml_include_tag.doc instead of the current source file.</span></span> <span data-ttu-id="e24da-127">Le compilateur génère ensuite DocFileName.xml, c’est-à-dire le fichier dont se servent les outils de documentation tels que [DocFX](https://dotnet.github.io/docfx/) et [Sandcastle](https://github.com/EWSoftware/SHFB) pour produire la documentation finale.</span><span class="sxs-lookup"><span data-stu-id="e24da-127">The compiler then generates DocFileName.xml, and this is the file that is consumed by documentation tools such as [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
```xml  
<?xml version="1.0"?>   
<doc>   
    <assembly>   
        <name>xml_include_tag</name>   
    </assembly>   
    <members>   
        <member name="T:Test">   
            <summary>   
The summary for this type.   
</summary>   
        </member>   
        <member name="T:Test2">   
            <summary>   
The summary for this other type.   
</summary>   
        </member>   
    </members>   
</doc>   
```  
  
## <a name="see-also"></a><span data-ttu-id="e24da-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e24da-128">See also</span></span>

- [<span data-ttu-id="e24da-129">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="e24da-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e24da-130">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="e24da-130">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
