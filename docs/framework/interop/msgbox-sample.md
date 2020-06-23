---
title: MsgBox, exemple
description: Consultez un exemple de passage de types chaîne par valeurs comme paramètres in à l’aide de MsgBox. Il indique quand utiliser les champs EntryPoint, CharSet et ExactSpelling dans .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
ms.openlocfilehash: ccf882e1f801dd18e5b65a4279fc580d927dd29d
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904089"
---
# <a name="msgbox-sample"></a><span data-ttu-id="b86e7-104">MsgBox, exemple</span><span class="sxs-lookup"><span data-stu-id="b86e7-104">MsgBox Sample</span></span>
<span data-ttu-id="b86e7-105">Cet exemple montre comment passer des types chaîne par valeur comme paramètres entrants, et quand utiliser les champs <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> et <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>.</span><span class="sxs-lookup"><span data-stu-id="b86e7-105">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="b86e7-106">L’exemple MsgBox utilise la fonction non managée suivante, accompagnée de sa déclaration de fonction d’origine :</span><span class="sxs-lookup"><span data-stu-id="b86e7-106">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
- <span data-ttu-id="b86e7-107">**MessageBox** exportée depuis User32.dll.</span><span class="sxs-lookup"><span data-stu-id="b86e7-107">**MessageBox** exported from User32.dll.</span></span>  
  
    ```cpp
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,
       UINT uType);  
    ```  
  
 <span data-ttu-id="b86e7-108">Dans cet exemple, la classe `NativeMethods` contient un prototype managé pour chaque fonction non managée appelée par la classe `MsgBoxSample`.</span><span class="sxs-lookup"><span data-stu-id="b86e7-108">In this sample, the `NativeMethods` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="b86e7-109">Les méthodes du prototype managé `MsgBox`, `MsgBox2` et `MsgBox3` ont des déclarations différentes pour la même fonction non managée.</span><span class="sxs-lookup"><span data-stu-id="b86e7-109">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="b86e7-110">La déclaration pour `MsgBox2` produit un résultat incorrect dans la boîte de message, car le type de caractère, spécifié comme étant ANSI, ne correspond pas au point d’entrée de `MessageBoxW`, qui est le nom de la fonction Unicode.</span><span class="sxs-lookup"><span data-stu-id="b86e7-110">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="b86e7-111">La déclaration pour `MsgBox3` crée une non-correspondance entre les champs **EntryPoint**, **CharSet** et **ExactSpelling**.</span><span class="sxs-lookup"><span data-stu-id="b86e7-111">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="b86e7-112">Quand elle est appelée, `MsgBox3` lève une exception.</span><span class="sxs-lookup"><span data-stu-id="b86e7-112">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="b86e7-113">Pour plus d’informations sur le nommage des chaînes et le marshaling des noms, consultez [Spécification d’un jeu de caractères](specifying-a-character-set.md).</span><span class="sxs-lookup"><span data-stu-id="b86e7-113">For detailed information on string naming and name marshaling, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="b86e7-114">Déclaration de prototypes</span><span class="sxs-lookup"><span data-stu-id="b86e7-114">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="b86e7-115">Appel de fonctions</span><span class="sxs-lookup"><span data-stu-id="b86e7-115">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="b86e7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b86e7-116">See also</span></span>

- [<span data-ttu-id="b86e7-117">Marshaling de chaînes</span><span class="sxs-lookup"><span data-stu-id="b86e7-117">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="b86e7-118">Marshaling par défaut pour les chaînes</span><span class="sxs-lookup"><span data-stu-id="b86e7-118">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
- [<span data-ttu-id="b86e7-119">Création de prototypes dans du code managé</span><span class="sxs-lookup"><span data-stu-id="b86e7-119">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="b86e7-120">Spécification d'un jeu de caractères</span><span class="sxs-lookup"><span data-stu-id="b86e7-120">Specifying a Character Set</span></span>](specifying-a-character-set.md)
