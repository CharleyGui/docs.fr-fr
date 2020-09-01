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
ms.openlocfilehash: f68652e910651ab5c4184376d9eb7729303382d9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124849"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="c93bb-103">-preferreduilang (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="c93bb-103">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="c93bb-104">L’option de compilateur `-preferreduilang` vous permet de spécifier la langue dans laquelle le compilateur C# affiche la sortie, comme les messages d’erreur.</span><span class="sxs-lookup"><span data-stu-id="c93bb-104">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c93bb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c93bb-105">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="c93bb-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="c93bb-106">Arguments</span></span>  
 `language`  
 <span data-ttu-id="c93bb-107">Le [nom de la langue](/windows/desktop/Intl/language-names) à utiliser pour la sortie du compilateur.</span><span class="sxs-lookup"><span data-stu-id="c93bb-107">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c93bb-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="c93bb-108">Remarks</span></span>  
 <span data-ttu-id="c93bb-109">Vous pouvez utiliser l’option de compilateur `-preferreduilang` pour spécifier la langue que le compilateur C# doit utiliser pour les messages d’erreur et d’autres types de sortie de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="c93bb-109">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="c93bb-110">Si le module linguistique de la langue n’est pas installé, le paramètre de langue du système d’exploitation est utilisé et aucune erreur n’est signalée.</span><span class="sxs-lookup"><span data-stu-id="c93bb-110">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="c93bb-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c93bb-111">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c93bb-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c93bb-112">See also</span></span>

- [<span data-ttu-id="c93bb-113">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="c93bb-113">C# Compiler Options</span></span>](./index.md)
