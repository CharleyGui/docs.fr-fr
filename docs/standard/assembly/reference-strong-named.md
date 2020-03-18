---
title: 'Comment : Référencez une assemblée forte'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: adda4ed2ab5c59e3518b8e724044529a79840ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156476"
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="7aef6-102">Comment : Référencez une assemblée forte</span><span class="sxs-lookup"><span data-stu-id="7aef6-102">How to: Reference a strong-named assembly</span></span>
<span data-ttu-id="7aef6-103">Le référencement de types ou de ressources dans un assembly avec nom fort est généralement un processus transparent.</span><span class="sxs-lookup"><span data-stu-id="7aef6-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="7aef6-104">Vous pouvez effectuer la référence au moment de la compilation (liaison anticipée) ou au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="7aef6-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
<span data-ttu-id="7aef6-105">Une référence de compilation-temps se produit lorsque vous indiquez au compilateur que l’assemblage à rassembler fait explicitement référence à une autre assemblée.</span><span class="sxs-lookup"><span data-stu-id="7aef6-105">A compile-time reference occurs when you indicate to the compiler that the assembly to be compiled explicitly references another assembly.</span></span> <span data-ttu-id="7aef6-106">Quand vous utilisez le référencement au moment de la compilation, le compilateur obtient automatiquement la clé publique de l’assembly avec nom fort ciblé et la place dans la référence d’assembly de l’assembly compilé.</span><span class="sxs-lookup"><span data-stu-id="7aef6-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>
  
> [!NOTE]
> <span data-ttu-id="7aef6-107">Un assembly avec nom fort peut uniquement utiliser les types d'autres assemblys avec nom fort.</span><span class="sxs-lookup"><span data-stu-id="7aef6-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="7aef6-108">Si ce n'était pas le cas, la sécurité de l'assembly avec nom fort serait compromise.</span><span class="sxs-lookup"><span data-stu-id="7aef6-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="7aef6-109">Faites une référence en temps de compilation à un assemblage fort</span><span class="sxs-lookup"><span data-stu-id="7aef6-109">Make a compile-time reference to a strong-named assembly</span></span>  

<span data-ttu-id="7aef6-110">Saisissez ensuite la commande suivante dans une invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="7aef6-110">At a command prompt, type the following command:</span></span>  

<span data-ttu-id="7aef6-111">\<*commande*> de compilateur **/référence :**\<*nom d’assemblage*></span><span class="sxs-lookup"><span data-stu-id="7aef6-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  

<span data-ttu-id="7aef6-112">Dans cette commande, *commande_compilateur* est la commande du compilateur pour le langage que vous utilisez, et *nom_assembly* est le nom de l’assembly avec nom fort référencé.</span><span class="sxs-lookup"><span data-stu-id="7aef6-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="7aef6-113">Vous pouvez également utiliser d’autres options du compilateur, telles que **/t:library**, qui permet de créer un assembly de bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="7aef6-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  

<span data-ttu-id="7aef6-114">L’exemple suivant crée une assemblée appelée *myAssembly.dll* qui fait référence à une assemblée forte appelée *myLibAssembly.dll* à partir d’un module de code appelé *myAssembly.cs*.</span><span class="sxs-lookup"><span data-stu-id="7aef6-114">The following example creates an assembly called *myAssembly.dll* that references a strong-named assembly called *myLibAssembly.dll* from a code module called *myAssembly.cs*.</span></span>  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="7aef6-115">Faites une référence en temps de course à un assemblage fort</span><span class="sxs-lookup"><span data-stu-id="7aef6-115">Make a run-time reference to a strong-named assembly</span></span>  
  
<span data-ttu-id="7aef6-116">Lorsque vous faites une référence en temps de course à <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> un <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> assemblage fort, par exemple en utilisant le ou la méthode, vous devez utiliser le nom d’affichage de l’assemblage référencé fort nommé.</span><span class="sxs-lookup"><span data-stu-id="7aef6-116">When you make a run-time reference to a strong-named assembly, for example by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method, you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="7aef6-117">La syntaxe d’un nom complet est la suivante :</span><span class="sxs-lookup"><span data-stu-id="7aef6-117">The syntax of a display name is as follows:</span></span>  

<span data-ttu-id="7aef6-118">\<*nom*>de l’assemblée **,** \< *numéro*>de version **,** \< *culture*>**,** \<jet de clé *publique*></span><span class="sxs-lookup"><span data-stu-id="7aef6-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  

<span data-ttu-id="7aef6-119">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="7aef6-119">For example:</span></span>  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33
```  

<span data-ttu-id="7aef6-120">Dans cet exemple, `PublicKeyToken` est la forme hexadécimale du jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="7aef6-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="7aef6-121">S’il n’existe aucune valeur de culture, utilisez `Culture=neutral`.</span><span class="sxs-lookup"><span data-stu-id="7aef6-121">If there is no culture value, use `Culture=neutral`.</span></span>  

<span data-ttu-id="7aef6-122">L’exemple de code suivant montre comment utiliser ces informations avec la méthode <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7aef6-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  

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

<span data-ttu-id="7aef6-123">Vous pouvez imprimer le format hexadécimal de la clé publique et du jeton de clé publique pour un assembly spécifique en utilisant la commande [Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) suivante :</span><span class="sxs-lookup"><span data-stu-id="7aef6-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  

<span data-ttu-id="7aef6-124">**sn \< -Tp** *assemblage\*\*\*>*\*</span><span class="sxs-lookup"><span data-stu-id="7aef6-124">**sn -Tp \<** *assembly* **>**</span></span>  

<span data-ttu-id="7aef6-125">Si vous avez un fichier de clé publique, vous pouvez utiliser la commande suivante (notez la différence de casse de l’option de ligne de commande) à la place :</span><span class="sxs-lookup"><span data-stu-id="7aef6-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  

<span data-ttu-id="7aef6-126">**sn -tp \<** *fichier de clé publique* **>**</span><span class="sxs-lookup"><span data-stu-id="7aef6-126">**sn -tp \<** *public key file* **>**</span></span>  

## <a name="see-also"></a><span data-ttu-id="7aef6-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7aef6-127">See also</span></span>

- [<span data-ttu-id="7aef6-128">Créer et utiliser des assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="7aef6-128">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
