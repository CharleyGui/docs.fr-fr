---
title: Délimiteurs pour les balises de documentation-Guide de programmation C#
ms.date: 07/20/2015
helpviewer_keywords:
- XML [C#], delimiters
- /** */ delimiters for C# documentation tags
- /// delimiter for C# documentation
ms.assetid: 9b2bdd18-4f5c-4c0b-988e-fb992e0d233e
ms.openlocfilehash: db8d43edc8b7cb0066fd3afcb75a1852603e86c4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594424"
---
# <a name="delimiters-for-documentation-tags-c-programming-guide"></a><span data-ttu-id="aaf16-102">Délimiteurs pour les balises de documentation (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="aaf16-102">Delimiters for documentation tags (C# programming guide)</span></span>

<span data-ttu-id="aaf16-103">L’utilisation de commentaires de documentation XML exige des délimiteurs, qui indiquent au compilateur où un commentaire de documentation commence et se termine.</span><span class="sxs-lookup"><span data-stu-id="aaf16-103">The use of XML doc comments requires delimiters, which indicate to the compiler where a documentation comment begins and ends.</span></span> <span data-ttu-id="aaf16-104">Vous pouvez utiliser les genres de délimiteurs ci-dessous avec les balises de documentation XML :</span><span class="sxs-lookup"><span data-stu-id="aaf16-104">You can use the following kinds of delimiters with the XML documentation tags:</span></span>

- `///`

  <span data-ttu-id="aaf16-105">Délimiteur à une ligne.</span><span class="sxs-lookup"><span data-stu-id="aaf16-105">Single-line delimiter.</span></span> <span data-ttu-id="aaf16-106">Il s’agit de la forme qui est présentée dans les exemples de documentation et utilisée par les modèles de projet C#.</span><span class="sxs-lookup"><span data-stu-id="aaf16-106">This is the form that is shown in documentation examples and used by the C# project templates.</span></span> <span data-ttu-id="aaf16-107">Si un caractère espace blanc suit le délimiteur, ce caractère n’est pas inclus dans la sortie XML.</span><span class="sxs-lookup"><span data-stu-id="aaf16-107">If there is a white space character following the delimiter, that character is not included in the XML output.</span></span>

  > [!NOTE]
  > <span data-ttu-id="aaf16-108">L’environnement de développement intégré (IDE) de Visual Studio insère automatiquement `<summary>` les `</summary>` balises et et déplace le curseur dans ces balises après que vous avez tapé le `///` délimiteur dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="aaf16-108">The Visual Studio integrated development environment (IDE) automatically inserts the `<summary>` and `</summary>` tags and moves your cursor within these tags after you type the `///` delimiter in the code editor.</span></span> <span data-ttu-id="aaf16-109">Vous pouvez activer/désactiver cette fonctionnalité dans la [boîte de dialogue Options](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span><span class="sxs-lookup"><span data-stu-id="aaf16-109">You can turn this feature on or off in the [Options dialog box](/visualstudio/ide/reference/options-text-editor-csharp-advanced).</span></span>
  
- `/** */`

  <span data-ttu-id="aaf16-110">Séparateurs multilignes.</span><span class="sxs-lookup"><span data-stu-id="aaf16-110">Multiline delimiters.</span></span>

  <span data-ttu-id="aaf16-111">Certaines règles de mise en forme doivent être respectées lorsque vous utilisez les `/** */` délimiteurs :</span><span class="sxs-lookup"><span data-stu-id="aaf16-111">There are some formatting rules to follow when you use the `/** */` delimiters:</span></span>
  
  - <span data-ttu-id="aaf16-112">Sur la ligne qui contient le délimiteur `/**`, si le reste de la ligne n’est constitué que d’espace blanc, la ligne n’est pas traitée pour les commentaires.</span><span class="sxs-lookup"><span data-stu-id="aaf16-112">On the line that contains the `/**` delimiter, if the remainder of the line is white space, the line is not processed for comments.</span></span> <span data-ttu-id="aaf16-113">Si le premier caractère après le délimiteur `/**` est un espace blanc, celui-ci est ignoré et le reste de la ligne est traité.</span><span class="sxs-lookup"><span data-stu-id="aaf16-113">If the first character after the `/**` delimiter is white space, that white space character is ignored and the rest of the line is processed.</span></span> <span data-ttu-id="aaf16-114">Sinon, tout le texte de la ligne après le délimiteur `/**` est traité comme faisant partie du commentaire.</span><span class="sxs-lookup"><span data-stu-id="aaf16-114">Otherwise, the entire text of the line after the `/**` delimiter is processed as part of the comment.</span></span>

  - <span data-ttu-id="aaf16-115">Sur la ligne qui contient le délimiteur `*/`, s’il n’y a que des espaces blancs jusqu’au délimiteur `*/`, cette ligne est ignorée.</span><span class="sxs-lookup"><span data-stu-id="aaf16-115">On the line that contains the `*/` delimiter, if there is only white space up to the `*/` delimiter, that line is ignored.</span></span> <span data-ttu-id="aaf16-116">Dans le cas contraire, le texte sur la ligne jusqu’au `*/` délimiteur est traité dans le cadre du commentaire.</span><span class="sxs-lookup"><span data-stu-id="aaf16-116">Otherwise, the text on the line up to the `*/` delimiter is processed as part of the comment.</span></span>
  
  - <span data-ttu-id="aaf16-117">Pour les lignes situées après celle qui commence par le délimiteur `/**`, le compilateur recherche un modèle commun au début de chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="aaf16-117">For the lines after the one that begins with the `/**` delimiter, the compiler looks for a common pattern at the beginning of each line.</span></span> <span data-ttu-id="aaf16-118">Le modèle peut se composer d’un espace blanc facultatif et d’un astérisque (`*`), suivi d’autres espaces blancs facultatifs.</span><span class="sxs-lookup"><span data-stu-id="aaf16-118">The pattern can consist of optional white space and an asterisk (`*`), followed by more optional white space.</span></span> <span data-ttu-id="aaf16-119">Si le compilateur détecte un modèle commun au début de chaque ligne qui ne commence pas par le délimiteur `/**` ou `*/`, il ignore ce modèle pour chaque ligne.</span><span class="sxs-lookup"><span data-stu-id="aaf16-119">If the compiler finds a common pattern at the beginning of each line that does not begin with the `/**` delimiter or the `*/` delimiter, it ignores that pattern for each line.</span></span>

  <span data-ttu-id="aaf16-120">Les exemples suivants illustrent ces règles.</span><span class="sxs-lookup"><span data-stu-id="aaf16-120">The following examples illustrate these rules.</span></span>

  - <span data-ttu-id="aaf16-121">La seule partie du commentaire suivant traitée est la ligne qui commence par `<summary>` .</span><span class="sxs-lookup"><span data-stu-id="aaf16-121">The only part of the following comment that's processed is the line that begins with `<summary>`.</span></span> <span data-ttu-id="aaf16-122">Les trois formats de balise produisent les mêmes commentaires.</span><span class="sxs-lookup"><span data-stu-id="aaf16-122">The three tag formats produce the same comments.</span></span>

    ```csharp
    /** <summary>text</summary> */

    /**
    <summary>text</summary>
    */

    /**
     * <summary>text</summary>
    */
    ```

  - <span data-ttu-id="aaf16-123">Le compilateur identifie un modèle commun de « \* » au début des deuxième et troisième lignes.</span><span class="sxs-lookup"><span data-stu-id="aaf16-123">The compiler identifies a common pattern of " \* " at the beginning of the second and third lines.</span></span> <span data-ttu-id="aaf16-124">Le modèle n’est pas inclus dans la sortie.</span><span class="sxs-lookup"><span data-stu-id="aaf16-124">The pattern is not included in the output.</span></span>

    ```csharp
    /**
     * <summary>
     * text </summary>*/
    ```

  - <span data-ttu-id="aaf16-125">Le compilateur ne détecte aucun modèle commun dans le commentaire suivant, car le deuxième caractère sur la troisième ligne n’est pas un astérisque.</span><span class="sxs-lookup"><span data-stu-id="aaf16-125">The compiler finds no common pattern in the following comment because the second character on the third line is not an asterisk.</span></span> <span data-ttu-id="aaf16-126">Ainsi, tout le texte des deuxième et troisième lignes est traité comme faisant partie du commentaire.</span><span class="sxs-lookup"><span data-stu-id="aaf16-126">Therefore, all text on the second and third lines is processed as part of the comment.</span></span>

    ```csharp
    /**
     * <summary>
       text </summary>
    */
    ```

  - <span data-ttu-id="aaf16-127">Le compilateur ne détecte aucun modèle dans le commentaire suivant pour deux raisons.</span><span class="sxs-lookup"><span data-stu-id="aaf16-127">The compiler finds no pattern in the following comment for two reasons.</span></span> <span data-ttu-id="aaf16-128">Tout d’abord, le nombre d’espaces avant l’astérisque n’est pas cohérent.</span><span class="sxs-lookup"><span data-stu-id="aaf16-128">First, the number of spaces before the asterisk is not consistent.</span></span> <span data-ttu-id="aaf16-129">Ensuite, la cinquième ligne commence par une tabulation, qui ne correspond pas à des espaces.</span><span class="sxs-lookup"><span data-stu-id="aaf16-129">Second, the fifth line begins with a tab, which does not match spaces.</span></span> <span data-ttu-id="aaf16-130">Ainsi, tout le texte des lignes deux à cinq est traité comme faisant partie du commentaire.</span><span class="sxs-lookup"><span data-stu-id="aaf16-130">Therefore, all text from lines two through five is processed as part of the comment.</span></span>

    <!-- markdownlint-disable MD010 -->
    ```csharp
    /**
      * <summary>
      * text
     *  text2
        *  </summary>
    */
    ```
    <!-- markdownlint-enable MD010 -->

## <a name="see-also"></a><span data-ttu-id="aaf16-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aaf16-131">See also</span></span>

- [<span data-ttu-id="aaf16-132">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="aaf16-132">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="aaf16-133">Commentaires sur la documentation XML</span><span class="sxs-lookup"><span data-stu-id="aaf16-133">XML documentation comments</span></span>](./index.md)
- [<span data-ttu-id="aaf16-134">-doc (options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="aaf16-134">-doc (C# compiler options)</span></span>](../../language-reference/compiler-options/doc-compiler-option.md)
