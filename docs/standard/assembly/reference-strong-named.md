---
title: 'Comment : référencer un assembly avec nom fort'
description: Cet article explique comment référencer des types ou des ressources dans un assembly .NET avec nom fort, au moment de la compilation ou de l’exécution.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 919e4f4cf467e8fc28c3d007963393dad134ab57
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724050"
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="b1f3e-103">Comment : référencer un assembly avec nom fort</span><span class="sxs-lookup"><span data-stu-id="b1f3e-103">How to: Reference a strong-named assembly</span></span>

<span data-ttu-id="b1f3e-104">Le référencement de types ou de ressources dans un assembly avec nom fort est généralement un processus transparent.</span><span class="sxs-lookup"><span data-stu-id="b1f3e-104">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="b1f3e-105">Vous pouvez effectuer la référence au moment de la compilation (liaison anticipée) ou au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b1f3e-105">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
<span data-ttu-id="b1f3e-106">Une référence au moment de la compilation se produit lorsque vous indiquez au compilateur que l’assembly à compiler fait explicitement référence à un autre assembly.</span><span class="sxs-lookup"><span data-stu-id="b1f3e-106">A compile-time reference occurs when you indicate to the compiler that the assembly to be compiled explicitly references another assembly.</span></span> <span data-ttu-id="b1f3e-107">Quand vous utilisez le référencement au moment de la compilation, le compilateur obtient automatiquement la clé publique de l’assembly avec nom fort ciblé et la place dans la référence d’assembly de l’assembly compilé.</span><span class="sxs-lookup"><span data-stu-id="b1f3e-107">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b1f3e-108">Un assembly avec nom fort peut uniquement utiliser les types d'autres assemblys avec nom fort.</span><span class="sxs-lookup"><span data-stu-id="b1f3e-108">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="b1f3e-109">Si ce n'était pas le cas, la sécurité de l'assembly avec nom fort serait compromise.</span><span class="sxs-lookup"><span data-stu-id="b1f3e-109">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="b1f3e-110">Créer une référence au moment de la compilation à un assembly avec nom fort</span><span class="sxs-lookup"><span data-stu-id="b1f3e-110">Make a compile-time reference to a strong-named assembly</span></span>  

<span data-ttu-id="b1f3e-111">Saisissez ensuite la commande suivante dans une invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="b1f3e-111">At a command prompt, type the following command:</span></span>  

<span data-ttu-id="b1f3e-112">\<*compiler command*>**/Reference :**\<*assembly name*></span><span class="sxs-lookup"><span data-stu-id="b1f3e-112">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  

<span data-ttu-id="b1f3e-113">Dans cette commande, *commande_compilateur* est la commande du compilateur pour le langage que vous utilisez, et *nom_assembly* est le nom de l’assembly avec nom fort référencé.</span><span class="sxs-lookup"><span data-stu-id="b1f3e-113">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="b1f3e-114">Vous pouvez également utiliser d’autres options du compilateur, telles que **/t:library**, qui permet de créer un assembly de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="b1f3e-114">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  

<span data-ttu-id="b1f3e-115">L’exemple suivant crée un assembly appelé *myAssembly.dll* qui référence un assembly avec nom fort appelé *myLibAssembly.dll* à partir d’un module de code appelé *myAssembly.cs*.</span><span class="sxs-lookup"><span data-stu-id="b1f3e-115">The following example creates an assembly called *myAssembly.dll* that references a strong-named assembly called *myLibAssembly.dll* from a code module called *myAssembly.cs*.</span></span>  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="b1f3e-116">Effectuer une référence au moment de l’exécution à un assembly avec nom fort</span><span class="sxs-lookup"><span data-stu-id="b1f3e-116">Make a run-time reference to a strong-named assembly</span></span>  
  
<span data-ttu-id="b1f3e-117">Quand vous faites référence à un assembly avec nom fort, par exemple à l’aide de la <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> méthode ou <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> , vous devez utiliser le nom complet de l’assembly avec nom fort référencé.</span><span class="sxs-lookup"><span data-stu-id="b1f3e-117">When you make a run-time reference to a strong-named assembly, for example by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method, you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="b1f3e-118">La syntaxe d’un nom complet est la suivante :</span><span class="sxs-lookup"><span data-stu-id="b1f3e-118">The syntax of a display name is as follows:</span></span>  

<span data-ttu-id="b1f3e-119">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span><span class="sxs-lookup"><span data-stu-id="b1f3e-119">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  

<span data-ttu-id="b1f3e-120">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b1f3e-120">For example:</span></span>  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33
```  

<span data-ttu-id="b1f3e-121">Dans cet exemple, `PublicKeyToken` est la forme hexadécimale du jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="b1f3e-121">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="b1f3e-122">S’il n’existe aucune valeur de culture, utilisez `Culture=neutral`.</span><span class="sxs-lookup"><span data-stu-id="b1f3e-122">If there is no culture value, use `Culture=neutral`.</span></span>  

<span data-ttu-id="b1f3e-123">L’exemple de code suivant montre comment utiliser ces informations avec la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1f3e-123">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  

```cpp
Assembly^ myDll =
    Assembly::Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```csharp
Assembly myDll =
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```vb
Dim myDll As Assembly = _
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1")
```

<span data-ttu-id="b1f3e-124">Vous pouvez imprimer le format hexadécimal de la clé publique et du jeton de clé publique pour un assembly spécifique en utilisant la commande [Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) suivante :</span><span class="sxs-lookup"><span data-stu-id="b1f3e-124">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  

<span data-ttu-id="b1f3e-125">**SN-TP \<** *assembly* **>**</span><span class="sxs-lookup"><span data-stu-id="b1f3e-125">**sn -Tp \<** *assembly* **>**</span></span>  

<span data-ttu-id="b1f3e-126">Si vous avez un fichier de clé publique, vous pouvez utiliser la commande suivante (notez la différence de casse de l’option de ligne de commande) à la place :</span><span class="sxs-lookup"><span data-stu-id="b1f3e-126">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  

<span data-ttu-id="b1f3e-127">**SN-TP \<** *public key file* **>**</span><span class="sxs-lookup"><span data-stu-id="b1f3e-127">**sn -tp \<** *public key file* **>**</span></span>  

## <a name="see-also"></a><span data-ttu-id="b1f3e-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1f3e-128">See also</span></span>

- [<span data-ttu-id="b1f3e-129">Créer et utiliser des assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="b1f3e-129">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
