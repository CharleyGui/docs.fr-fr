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
ms.openlocfilehash: f3f9f5ecb96686fe525e98cf64672d81a3145796
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873274"
---
# <a name="error-statement"></a><span data-ttu-id="26664-102">Error, instruction</span><span class="sxs-lookup"><span data-stu-id="26664-102">Error Statement</span></span>

<span data-ttu-id="26664-103">Simule l’occurrence d’une erreur.</span><span class="sxs-lookup"><span data-stu-id="26664-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26664-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26664-104">Syntax</span></span>  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="26664-105">Éléments</span><span class="sxs-lookup"><span data-stu-id="26664-105">Parts</span></span>  

 `errornumber`  
 <span data-ttu-id="26664-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="26664-106">Required.</span></span> <span data-ttu-id="26664-107">Peut être n’importe quel numéro d’erreur valide.</span><span class="sxs-lookup"><span data-stu-id="26664-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26664-108">Notes</span><span class="sxs-lookup"><span data-stu-id="26664-108">Remarks</span></span>  

 <span data-ttu-id="26664-109">L' `Error` instruction est prise en charge pour la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="26664-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="26664-110">Dans le nouveau code, en particulier lors de la création d’objets, utilisez la `Err` méthode de l’objet `Raise` pour générer des erreurs au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="26664-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="26664-111">Si `errornumber` est défini, l' `Error` instruction appelle le gestionnaire d’erreurs après que les propriétés de l' `Err` objet reçoivent les valeurs par défaut suivantes :</span><span class="sxs-lookup"><span data-stu-id="26664-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="26664-112">Propriété</span><span class="sxs-lookup"><span data-stu-id="26664-112">Property</span></span>|<span data-ttu-id="26664-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="26664-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="26664-114">Valeur spécifiée comme argument de l' `Error` instruction.</span><span class="sxs-lookup"><span data-stu-id="26664-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="26664-115">Peut être n’importe quel numéro d’erreur valide.</span><span class="sxs-lookup"><span data-stu-id="26664-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="26664-116">Nom du projet de Visual Basic actif.</span><span class="sxs-lookup"><span data-stu-id="26664-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="26664-117">Expression de chaîne correspondant à la valeur de retour de la `Error` fonction pour le spécifié `Number` , si cette chaîne existe.</span><span class="sxs-lookup"><span data-stu-id="26664-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="26664-118">Si la chaîne n’existe pas, `Description` contient une chaîne de longueur nulle ("").</span><span class="sxs-lookup"><span data-stu-id="26664-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="26664-119">Le lecteur complet, le chemin d’accès et le nom de fichier du fichier d’aide Visual Basic approprié.</span><span class="sxs-lookup"><span data-stu-id="26664-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="26664-120">L’ID de contexte du fichier d’aide de Visual Basic approprié pour l’erreur correspondant à la `Number` propriété.</span><span class="sxs-lookup"><span data-stu-id="26664-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="26664-121">Zéro.</span><span class="sxs-lookup"><span data-stu-id="26664-121">Zero.</span></span>|  
  
 <span data-ttu-id="26664-122">Si aucun gestionnaire d’erreurs n’existe ou si aucun n’est activé, un message d’erreur est créé et affiché à partir des propriétés de l' `Err` objet.</span><span class="sxs-lookup"><span data-stu-id="26664-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="26664-123">Certaines applications hôtes Visual Basic ne peuvent pas créer d’objets.</span><span class="sxs-lookup"><span data-stu-id="26664-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="26664-124">Consultez la documentation de votre application hôte pour déterminer si elle peut créer des classes et des objets.</span><span class="sxs-lookup"><span data-stu-id="26664-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26664-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="26664-125">Example</span></span>  

 <span data-ttu-id="26664-126">L’exemple suivant utilise l' `Error` instruction pour générer le numéro d’erreur 11.</span><span class="sxs-lookup"><span data-stu-id="26664-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="26664-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="26664-127">Requirements</span></span>  

 <span data-ttu-id="26664-128">**Espace de noms :** [Microsoft. VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="26664-128">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="26664-129">**Assembly :** Visual Basic la bibliothèque Runtime (dans Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="26664-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26664-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26664-130">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="26664-131">On Error (instruction)</span><span class="sxs-lookup"><span data-stu-id="26664-131">On Error Statement</span></span>](on-error-statement.md)
- [<span data-ttu-id="26664-132">Resume, instruction</span><span class="sxs-lookup"><span data-stu-id="26664-132">Resume Statement</span></span>](resume-statement.md)
- [<span data-ttu-id="26664-133">Messages d’erreur</span><span class="sxs-lookup"><span data-stu-id="26664-133">Error Messages</span></span>](../error-messages/index.md)
