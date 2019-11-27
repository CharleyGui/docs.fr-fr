---
title: Error, instruction
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 668ffbc7b8db73a706c5771bb0734a77f8fc0206
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351239"
---
# <a name="error-statement"></a><span data-ttu-id="0773e-102">Error, instruction</span><span class="sxs-lookup"><span data-stu-id="0773e-102">Error Statement</span></span>
<span data-ttu-id="0773e-103">Simule l’occurrence d’une erreur.</span><span class="sxs-lookup"><span data-stu-id="0773e-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0773e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0773e-104">Syntax</span></span>  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="0773e-105">Composants</span><span class="sxs-lookup"><span data-stu-id="0773e-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="0773e-106">Requis.</span><span class="sxs-lookup"><span data-stu-id="0773e-106">Required.</span></span> <span data-ttu-id="0773e-107">Peut être n’importe quel numéro d’erreur valide.</span><span class="sxs-lookup"><span data-stu-id="0773e-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0773e-108">Notes</span><span class="sxs-lookup"><span data-stu-id="0773e-108">Remarks</span></span>  
 <span data-ttu-id="0773e-109">L’instruction `Error` est prise en charge pour la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="0773e-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="0773e-110">Dans le nouveau code, en particulier lors de la création d’objets, utilisez la méthode `Raise` de l’objet `Err` pour générer des erreurs d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0773e-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="0773e-111">Si `errornumber` est défini, l’instruction `Error` appelle le gestionnaire d’erreurs après que les propriétés de l’objet `Err` reçoivent les valeurs par défaut suivantes :</span><span class="sxs-lookup"><span data-stu-id="0773e-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="0773e-112">Propriété</span><span class="sxs-lookup"><span data-stu-id="0773e-112">Property</span></span>|<span data-ttu-id="0773e-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="0773e-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="0773e-114">Valeur spécifiée comme argument pour `Error` instruction.</span><span class="sxs-lookup"><span data-stu-id="0773e-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="0773e-115">Peut être n’importe quel numéro d’erreur valide.</span><span class="sxs-lookup"><span data-stu-id="0773e-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="0773e-116">Nom du projet de Visual Basic actif.</span><span class="sxs-lookup"><span data-stu-id="0773e-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="0773e-117">Expression de chaîne correspondant à la valeur de retour de la fonction `Error` pour le `Number`spécifié, si cette chaîne existe.</span><span class="sxs-lookup"><span data-stu-id="0773e-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="0773e-118">Si la chaîne n’existe pas, `Description` contient une chaîne de longueur nulle ("").</span><span class="sxs-lookup"><span data-stu-id="0773e-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="0773e-119">Le lecteur complet, le chemin d’accès et le nom de fichier du fichier d’aide Visual Basic approprié.</span><span class="sxs-lookup"><span data-stu-id="0773e-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="0773e-120">L’ID de contexte du fichier d’aide Visual Basic approprié pour l’erreur correspondant à la propriété `Number`.</span><span class="sxs-lookup"><span data-stu-id="0773e-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="0773e-121">Nuls.</span><span class="sxs-lookup"><span data-stu-id="0773e-121">Zero.</span></span>|  
  
 <span data-ttu-id="0773e-122">Si aucun gestionnaire d’erreurs n’existe ou si aucun n’est activé, un message d’erreur est créé et affiché à partir des propriétés de l’objet `Err`.</span><span class="sxs-lookup"><span data-stu-id="0773e-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0773e-123">Certaines applications hôtes Visual Basic ne peuvent pas créer d’objets.</span><span class="sxs-lookup"><span data-stu-id="0773e-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="0773e-124">Consultez la documentation de votre application hôte pour déterminer si elle peut créer des classes et des objets.</span><span class="sxs-lookup"><span data-stu-id="0773e-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0773e-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="0773e-125">Example</span></span>  
 <span data-ttu-id="0773e-126">L’exemple suivant utilise l’instruction `Error` pour générer le numéro d’erreur 11.</span><span class="sxs-lookup"><span data-stu-id="0773e-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="0773e-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0773e-127">Requirements</span></span>  
 <span data-ttu-id="0773e-128">**Espace de noms :** [Microsoft. VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="0773e-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="0773e-129">**Assembly :** Visual Basic bibliothèque Runtime (dans Microsoft. VisualBasic. dll)</span><span class="sxs-lookup"><span data-stu-id="0773e-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0773e-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0773e-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="0773e-131">On Error (instruction)</span><span class="sxs-lookup"><span data-stu-id="0773e-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
- [<span data-ttu-id="0773e-132">Resume (instruction)</span><span class="sxs-lookup"><span data-stu-id="0773e-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="0773e-133">Messages d’erreur</span><span class="sxs-lookup"><span data-stu-id="0773e-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
