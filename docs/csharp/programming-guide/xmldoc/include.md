---
title: <include> -Guide de programmation C#
description: En savoir plus sur le XML <include> balise. Cette balise vous permet de faire référence aux commentaires d’un autre fichier qui décrivent les types et les membres de votre code source.
ms.date: 07/20/2015
f1_keywords:
- include
- <include>
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
ms.openlocfilehash: d2de8fea17850685668766bc4ec6e64b1be77cce
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053189"
---
# <a name="include-c-programming-guide"></a><span data-ttu-id="6e85c-105">\<include> (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="6e85c-105">\<include> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="6e85c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e85c-106">Syntax</span></span>

```xml
<include file='filename' path='tagpath[@name="id"]' />
```

## <a name="parameters"></a><span data-ttu-id="6e85c-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6e85c-107">Parameters</span></span>

- `filename`

  <span data-ttu-id="6e85c-108">Nom du fichier XML contenant la documentation.</span><span class="sxs-lookup"><span data-stu-id="6e85c-108">The name of the XML file containing the documentation.</span></span> <span data-ttu-id="6e85c-109">Le nom de fichier peut être qualifié avec un chemin relatif au fichier de code source.</span><span class="sxs-lookup"><span data-stu-id="6e85c-109">The file name can be qualified with a path relative to the source code file.</span></span> <span data-ttu-id="6e85c-110">Mettez `filename` entre guillemets simples (' ').</span><span class="sxs-lookup"><span data-stu-id="6e85c-110">Enclose `filename` in single quotation marks (' ').</span></span>

- `tagpath`

  <span data-ttu-id="6e85c-111">Chemin des balises contenues dans `filename` qui mène à la balise `name`.</span><span class="sxs-lookup"><span data-stu-id="6e85c-111">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="6e85c-112">Mettez le chemin entre guillemets simples (' ').</span><span class="sxs-lookup"><span data-stu-id="6e85c-112">Enclose the path in single quotation marks (' ').</span></span>

- `name`

  <span data-ttu-id="6e85c-113">Spécificateur de nom contenu dans la balise qui précède les commentaires ; `name` possède un `id`.</span><span class="sxs-lookup"><span data-stu-id="6e85c-113">The name specifier in the tag that precedes the comments; `name` will have an `id`.</span></span>

- `id`

  <span data-ttu-id="6e85c-114">ID de la balise qui précède les commentaires.</span><span class="sxs-lookup"><span data-stu-id="6e85c-114">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="6e85c-115">Mettez l’ID entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="6e85c-115">Enclose the ID in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="6e85c-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="6e85c-116">Remarks</span></span>

<span data-ttu-id="6e85c-117">La `<include>` balise vous permet de faire référence aux commentaires d’un autre fichier qui décrivent les types et les membres de votre code source.</span><span class="sxs-lookup"><span data-stu-id="6e85c-117">The `<include>` tag lets you refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="6e85c-118">Il s’agit d’une solution alternative au placement direct des commentaires de la documentation dans votre fichier de code source.</span><span class="sxs-lookup"><span data-stu-id="6e85c-118">This is an alternative to placing documentation comments directly in your source code file.</span></span> <span data-ttu-id="6e85c-119">En plaçant la documentation dans un fichier distinct, vous pouvez appliquer un contrôle de code source à la documentation indépendamment du code source.</span><span class="sxs-lookup"><span data-stu-id="6e85c-119">By putting the documentation in a separate file, you can apply source control to the documentation separately from the source code.</span></span> <span data-ttu-id="6e85c-120">Ainsi, une personne peut extraire le fichier de code source et une autre personne peut extraire le fichier de documentation.</span><span class="sxs-lookup"><span data-stu-id="6e85c-120">One person can have the source code file checked out and someone else can have the documentation file checked out.</span></span>

<span data-ttu-id="6e85c-121">La `<include>` balise utilise la syntaxe XML XPath.</span><span class="sxs-lookup"><span data-stu-id="6e85c-121">The `<include>` tag uses the XML XPath syntax.</span></span> <span data-ttu-id="6e85c-122">Reportez-vous à la documentation XPath pour savoir comment personnaliser votre `<include>` utilisation.</span><span class="sxs-lookup"><span data-stu-id="6e85c-122">Refer to XPath documentation for ways to customize your `<include>` use.</span></span>

## <a name="example"></a><span data-ttu-id="6e85c-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="6e85c-123">Example</span></span>

<span data-ttu-id="6e85c-124">Cet exemple comprend plusieurs fichiers.</span><span class="sxs-lookup"><span data-stu-id="6e85c-124">This is a multifile example.</span></span> <span data-ttu-id="6e85c-125">Voici le premier fichier, qui utilise `<include>` .</span><span class="sxs-lookup"><span data-stu-id="6e85c-125">The following is the first file, which uses `<include>`.</span></span>

[!code-csharp[csProgGuideDocComments#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#5)]

<span data-ttu-id="6e85c-126">Le deuxième fichier, *xml_include_tag.doc*, contient les commentaires de documentation suivants.</span><span class="sxs-lookup"><span data-stu-id="6e85c-126">The second file, *xml_include_tag.doc*, contains the following documentation comments.</span></span>

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

## <a name="program-output"></a><span data-ttu-id="6e85c-127">Sortie du programme</span><span class="sxs-lookup"><span data-stu-id="6e85c-127">Program output</span></span>

<span data-ttu-id="6e85c-128">La sortie suivante est générée quand vous compilez les classes Test et Test2 avec la ligne de commande suivante : `-doc:DocFileName.xml.` Dans Visual Studio, l’option de commentaires de document XML est spécifiée dans le volet de génération du Concepteur de projet.</span><span class="sxs-lookup"><span data-stu-id="6e85c-128">The following output is generated when you compile the Test and Test2 classes with the following command line: `-doc:DocFileName.xml.` In Visual Studio, you specify the XML doc comments option in the Build pane of the Project Designer.</span></span> <span data-ttu-id="6e85c-129">Lorsque le compilateur C# voit la `<include>` balise, il recherche des commentaires de documentation dans *xml_include_tag.doc* au lieu du fichier source actuel.</span><span class="sxs-lookup"><span data-stu-id="6e85c-129">When the C# compiler sees the `<include>` tag, it searches for documentation comments in *xml_include_tag.doc* instead of the current source file.</span></span> <span data-ttu-id="6e85c-130">Le compilateur génère ensuite *DocFileName.xml*, et il s’agit du fichier utilisé par les outils de documentation tels que [Sandcastle](https://github.com/EWSoftware/SHFB) pour produire la documentation finale.</span><span class="sxs-lookup"><span data-stu-id="6e85c-130">The compiler then generates *DocFileName.xml*, and this is the file that is consumed by documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to produce the final documentation.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6e85c-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e85c-131">See also</span></span>

- [<span data-ttu-id="6e85c-132">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="6e85c-132">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6e85c-133">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="6e85c-133">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
