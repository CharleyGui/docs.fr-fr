---
title: Les références d'entité XML ne sont pas prises en charge
ms.date: 07/20/2015
f1_keywords:
- vbc31180
- bc31180
helpviewer_keywords:
- BC31180
ms.assetid: 2a393327-d8e2-4187-85b1-642b4f53b4ae
ms.openlocfilehash: 37e72dbd6de61a50b4192a0151db40cb4be49d1c
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163270"
---
# <a name="bc31180-xml-entity-references-are-not-supported"></a><span data-ttu-id="57b8b-102">BC31180 : les références d’entité XML ne sont pas prises en charge</span><span class="sxs-lookup"><span data-stu-id="57b8b-102">BC31180: XML entity references are not supported</span></span>

<span data-ttu-id="57b8b-103">Une référence d’entité (par exemple, `©` ) qui n’est pas définie dans la spécification xml 1,0 est incluse comme valeur pour un LITTÉRAL XML.</span><span class="sxs-lookup"><span data-stu-id="57b8b-103">An entity reference (for example, `©`) that is not defined in the XML 1.0 specification is included as a value for an XML literal.</span></span> <span data-ttu-id="57b8b-104">Seules `&` `"` `<` `>` `'` les références d’entité XML,,, et sont prises en charge dans les littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="57b8b-104">Only `&`, `"`, `<`, `>`, and `'` XML entity references are supported in XML literals.</span></span>

 <span data-ttu-id="57b8b-105">**ID d’erreur :** BC31180</span><span class="sxs-lookup"><span data-stu-id="57b8b-105">**Error ID:** BC31180</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="57b8b-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="57b8b-106">To correct this error</span></span>

- <span data-ttu-id="57b8b-107">Supprimez la référence d’entité non prise en charge.</span><span class="sxs-lookup"><span data-stu-id="57b8b-107">Remove the unsupported entity reference.</span></span>

## <a name="see-also"></a><span data-ttu-id="57b8b-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57b8b-108">See also</span></span>

- [<span data-ttu-id="57b8b-109">Littéraux XML et spécification XML 1.0</span><span class="sxs-lookup"><span data-stu-id="57b8b-109">XML Literals and the XML 1.0 Specification</span></span>](../../programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md)
- [<span data-ttu-id="57b8b-110">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="57b8b-110">XML Literals</span></span>](../xml-literals/index.md)
- [<span data-ttu-id="57b8b-111">XML</span><span class="sxs-lookup"><span data-stu-id="57b8b-111">XML</span></span>](../../programming-guide/language-features/xml/index.md)
