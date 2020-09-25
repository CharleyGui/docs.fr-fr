---
description: -preferreduilang (Options du compilateur C#)
title: -preferreduilang (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: 490f5926fb50cfdae740b7749d72ea6c9a1f8cc9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193814"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="4a38e-103">-preferreduilang (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="4a38e-103">-preferreduilang (C# Compiler Options)</span></span>

<span data-ttu-id="4a38e-104">L’option de compilateur `-preferreduilang` vous permet de spécifier la langue dans laquelle le compilateur C# affiche la sortie, comme les messages d’erreur.</span><span class="sxs-lookup"><span data-stu-id="4a38e-104">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a38e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a38e-105">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="4a38e-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="4a38e-106">Arguments</span></span>  

 `language`  
 <span data-ttu-id="4a38e-107">Le [nom de la langue](/windows/desktop/Intl/language-names) à utiliser pour la sortie du compilateur.</span><span class="sxs-lookup"><span data-stu-id="4a38e-107">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a38e-108">Notes</span><span class="sxs-lookup"><span data-stu-id="4a38e-108">Remarks</span></span>  

 <span data-ttu-id="4a38e-109">Vous pouvez utiliser l’option de compilateur `-preferreduilang` pour spécifier la langue que le compilateur C# doit utiliser pour les messages d’erreur et d’autres types de sortie de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="4a38e-109">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="4a38e-110">Si le module linguistique de la langue n’est pas installé, le paramètre de langue du système d’exploitation est utilisé et aucune erreur n’est signalée.</span><span class="sxs-lookup"><span data-stu-id="4a38e-110">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="4a38e-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4a38e-111">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a38e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a38e-112">See also</span></span>

- [<span data-ttu-id="4a38e-113">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="4a38e-113">C# Compiler Options</span></span>](./index.md)
