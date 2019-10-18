---
title: <permission> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 904d573514bf35b773d47321b7fd3b6a86e90262
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524704"
---
# <a name="permission-visual-basic"></a><span data-ttu-id="ba132-102">> \<permission (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba132-102">\<permission> (Visual Basic)</span></span>
<span data-ttu-id="ba132-103">Spécifie une autorisation requise pour le membre.</span><span class="sxs-lookup"><span data-stu-id="ba132-103">Specifies a required permission for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba132-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba132-104">Syntax</span></span>  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba132-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ba132-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="ba132-106">Référence à un membre ou à un champ qui peut être appelé à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="ba132-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="ba132-107">Le compilateur vérifie que l’élément de code donné existe et traduit `member` en nom d’élément canonique dans le fichier XML de sortie.</span><span class="sxs-lookup"><span data-stu-id="ba132-107">The compiler checks that the given code element exists and translates `member` to the canonical element name in the output XML.</span></span> <span data-ttu-id="ba132-108">Placez `member` entre guillemets ("").</span><span class="sxs-lookup"><span data-stu-id="ba132-108">Enclose `member` in quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="ba132-109">Description de l’accès au membre.</span><span class="sxs-lookup"><span data-stu-id="ba132-109">A description of the access to the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba132-110">Notes</span><span class="sxs-lookup"><span data-stu-id="ba132-110">Remarks</span></span>  
 <span data-ttu-id="ba132-111">Utilisez la balise `<permission>` pour documenter l’accès d’un membre.</span><span class="sxs-lookup"><span data-stu-id="ba132-111">Use the `<permission>` tag to document the access of a member.</span></span> <span data-ttu-id="ba132-112">Utilisez la classe <xref:System.Security.PermissionSet> pour spécifier l’accès à un membre.</span><span class="sxs-lookup"><span data-stu-id="ba132-112">Use the <xref:System.Security.PermissionSet> class to specify access to a member.</span></span>  
  
 <span data-ttu-id="ba132-113">Compilez avec [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="ba132-113">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba132-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="ba132-114">Example</span></span>  
 <span data-ttu-id="ba132-115">Cet exemple utilise la balise `<permission>` pour décrire que la <xref:System.Security.Permissions.FileIOPermission> est requise par la méthode `ReadFile`.</span><span class="sxs-lookup"><span data-stu-id="ba132-115">This example uses the `<permission>` tag to describe that the <xref:System.Security.Permissions.FileIOPermission> is required by the `ReadFile` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="ba132-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba132-116">See also</span></span>

- [<span data-ttu-id="ba132-117">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="ba132-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
