---
title: <param>
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: d325d5f9fbfd132630cf280653be214a267a7a80
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400058"
---
# <a name="param-visual-basic"></a><span data-ttu-id="2f8ee-101">\<param> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f8ee-101">\<param> (Visual Basic)</span></span>
<span data-ttu-id="2f8ee-102">Définit un nom de paramètre et une description.</span><span class="sxs-lookup"><span data-stu-id="2f8ee-102">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f8ee-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f8ee-103">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f8ee-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2f8ee-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="2f8ee-105">Nom d’un paramètre de méthode.</span><span class="sxs-lookup"><span data-stu-id="2f8ee-105">The name of a method parameter.</span></span> <span data-ttu-id="2f8ee-106">Mettez le nom entre guillemets doubles (" ").</span><span class="sxs-lookup"><span data-stu-id="2f8ee-106">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="2f8ee-107">Description du paramètre.</span><span class="sxs-lookup"><span data-stu-id="2f8ee-107">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f8ee-108">Notes</span><span class="sxs-lookup"><span data-stu-id="2f8ee-108">Remarks</span></span>  
 <span data-ttu-id="2f8ee-109">La `<param>` balise doit être utilisée dans le commentaire d’une déclaration de méthode pour décrire l’un des paramètres de la méthode.</span><span class="sxs-lookup"><span data-stu-id="2f8ee-109">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="2f8ee-110">Le texte de la `<param>` balise apparaît aux emplacements suivants :</span><span class="sxs-lookup"><span data-stu-id="2f8ee-110">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
- <span data-ttu-id="2f8ee-111">Informations sur les paramètres d’IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="2f8ee-111">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="2f8ee-112">Pour plus d’informations, consultez [Utilisation d’IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="2f8ee-112">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
- <span data-ttu-id="2f8ee-113">Explorateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="2f8ee-113">Object Browser.</span></span> <span data-ttu-id="2f8ee-114">Pour plus d’informations, consultez [affichage de la structure du code](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="2f8ee-114">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="2f8ee-115">Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="2f8ee-115">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f8ee-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="2f8ee-116">Example</span></span>  
 <span data-ttu-id="2f8ee-117">Cet exemple utilise la `<param>` balise pour décrire le `id` paramètre.</span><span class="sxs-lookup"><span data-stu-id="2f8ee-117">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="2f8ee-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f8ee-118">See also</span></span>

- [<span data-ttu-id="2f8ee-119">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="2f8ee-119">XML Comment Tags</span></span>](index.md)
