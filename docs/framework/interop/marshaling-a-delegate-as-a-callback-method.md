---
title: Marshaling d'un délégué comme méthode de rappel
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
ms.openlocfilehash: c71c89e5797745144a2baed2d4846e3d9f9f26be
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114015"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="39381-102">Marshaling d'un délégué comme méthode de rappel</span><span class="sxs-lookup"><span data-stu-id="39381-102">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="39381-103">Cet exemple montre comment passer des délégués à une fonction non managée qui attend des pointeurs de fonction.</span><span class="sxs-lookup"><span data-stu-id="39381-103">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="39381-104">Un délégué est une classe qui peut contenir une référence à une méthode, et qui équivaut à un pointeur de fonction de type sécurisé ou à une fonction de rappel.</span><span class="sxs-lookup"><span data-stu-id="39381-104">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>

> [!NOTE]
> <span data-ttu-id="39381-105">Quand vous utilisez un délégué à l’intérieur d’un appel, le common language runtime protège le délégué d’une garbage collection pendant la durée de cet appel.</span><span class="sxs-lookup"><span data-stu-id="39381-105">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="39381-106">Cependant, si la fonction non managée stocke le délégué pour l’utiliser une fois l’appel terminé, vous devez empêcher manuellement la garbage collection jusqu’à ce que la fonction non managée en termine avec le délégué.</span><span class="sxs-lookup"><span data-stu-id="39381-106">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="39381-107">Pour plus d’informations, consultez [HandleRef, exemple](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) et [GCHandle, exemple](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="39381-107">For more information, see the [HandleRef Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) and [GCHandle Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span></span>

<span data-ttu-id="39381-108">L’exemple de rappel utilise les fonctions non managées suivantes, qui sont montrées avec leur déclaration de fonction d’origine :</span><span class="sxs-lookup"><span data-stu-id="39381-108">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="39381-109">`TestCallBack` exportée depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="39381-109">`TestCallBack` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack(FPTR pf, int value);
    ```

- <span data-ttu-id="39381-110">`TestCallBack2` exportée depuis PinvokeLib.dll.</span><span class="sxs-lookup"><span data-stu-id="39381-110">`TestCallBack2` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack2(FPTR2 pf2, char* value);
    ```

<span data-ttu-id="39381-111">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) est une bibliothèque non managée personnalisée qui contient une implémentation des fonctions précédemment répertoriées.</span><span class="sxs-lookup"><span data-stu-id="39381-111">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>

<span data-ttu-id="39381-112">Dans cet exemple, la classe `NativeMethods` contient des prototypes managés pour les méthodes `TestCallBack` et `TestCallBack2`.</span><span class="sxs-lookup"><span data-stu-id="39381-112">In this sample, the `NativeMethods` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="39381-113">Ces deux méthodes passent un délégué comme paramètre à une fonction de rappel.</span><span class="sxs-lookup"><span data-stu-id="39381-113">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="39381-114">La signature du délégué doit correspondre à la signature de la méthode qu’il référence.</span><span class="sxs-lookup"><span data-stu-id="39381-114">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="39381-115">Par exemple, les délégués `FPtr` et `FPtr2` ont des signatures qui sont identiques à celles des méthodes `DoSomething` et `DoSomething2`.</span><span class="sxs-lookup"><span data-stu-id="39381-115">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>

## <a name="declaring-prototypes"></a><span data-ttu-id="39381-116">Déclaration de prototypes</span><span class="sxs-lookup"><span data-stu-id="39381-116">Declaring Prototypes</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
[!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
[!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]

## <a name="calling-functions"></a><span data-ttu-id="39381-117">Appel de fonctions</span><span class="sxs-lookup"><span data-stu-id="39381-117">Calling Functions</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
[!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
[!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]

## <a name="see-also"></a><span data-ttu-id="39381-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39381-118">See also</span></span>

- <span data-ttu-id="39381-119">[Exemples divers de marshaling](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="39381-119">[Miscellaneous Marshaling Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span></span>
- [<span data-ttu-id="39381-120">Types de données d’appel de code non managé</span><span class="sxs-lookup"><span data-stu-id="39381-120">Platform Invoke Data Types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="39381-121">Création de prototypes dans du code managé</span><span class="sxs-lookup"><span data-stu-id="39381-121">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
