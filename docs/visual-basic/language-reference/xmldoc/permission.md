---
title: <permission>
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: b3acec04060367a0b9e54b19c0106644d028357b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400032"
---
# <a name="permission-visual-basic"></a><span data-ttu-id="89a1a-101">\<permission> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89a1a-101">\<permission> (Visual Basic)</span></span>
<span data-ttu-id="89a1a-102">Spécifie une autorisation requise pour le membre.</span><span class="sxs-lookup"><span data-stu-id="89a1a-102">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89a1a-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89a1a-103">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="89a1a-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="89a1a-104">Parameters</span></span>  
 `member`  
 <span data-ttu-id="89a1a-105">Référence à un membre ou un champ qu’il est possible d’appeler à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="89a1a-105">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="89a1a-106">Le compilateur vérifie que l’élément de code donné existe et traduit `member` en nom d’élément canonique dans le fichier XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="89a1a-106">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="89a1a-107">Mettez `member` entre guillemets ("").</span><span class="sxs-lookup"><span data-stu-id="89a1a-107">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="89a1a-108">Description de l’accès au membre.</span><span class="sxs-lookup"><span data-stu-id="89a1a-108">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89a1a-109">Notes</span><span class="sxs-lookup"><span data-stu-id="89a1a-109">Remarks</span></span>  
 <span data-ttu-id="89a1a-110">Utilisez la `<permission>` balise pour documenter l’accès d’un membre.</span><span class="sxs-lookup"><span data-stu-id="89a1a-110">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="89a1a-111">Utilisez la <xref:System.Security.PermissionSet> classe pour spécifier l’accès à un membre.</span><span class="sxs-lookup"><span data-stu-id="89a1a-111">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="89a1a-112">Compilez avec [-doc](../../reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="89a1a-112">Compile with [-doc](../../reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89a1a-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="89a1a-113">Example</span></span>  
 <span data-ttu-id="89a1a-114">Cet exemple utilise la `<permission>` balise pour décrire que <xref:System.Security.Permissions.FileIOPermission> est requis par la `ReadFile` méthode.</span><span class="sxs-lookup"><span data-stu-id="89a1a-114">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="89a1a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89a1a-115">See also</span></span>

- [<span data-ttu-id="89a1a-116">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="89a1a-116">XML Comment Tags</span></span>](index.md)
