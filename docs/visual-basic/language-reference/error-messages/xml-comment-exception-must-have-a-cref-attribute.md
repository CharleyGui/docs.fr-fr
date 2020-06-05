---
title: L'exception de commentaire XML doit avoir un attribut 'cref'
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: c498675ab6ae616fb63d3d76ef60bcac7e247145
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406506"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="2ea2e-102">L'exception de commentaire XML doit avoir un attribut 'cref'</span><span class="sxs-lookup"><span data-stu-id="2ea2e-102">XML comment exception must have a 'cref' attribute</span></span>

<span data-ttu-id="2ea2e-103">La \<exception> balise permet de documenter les exceptions qui peuvent être levées par une méthode.</span><span class="sxs-lookup"><span data-stu-id="2ea2e-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="2ea2e-104">L’attribut required `cref` désigne le nom d’un membre, qui est vérifié par le générateur de documentation.</span><span class="sxs-lookup"><span data-stu-id="2ea2e-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="2ea2e-105">Si le membre existe, il est traduit en nom d’élément canonique dans le fichier de documentation.</span><span class="sxs-lookup"><span data-stu-id="2ea2e-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>

<span data-ttu-id="2ea2e-106">**ID d’erreur :** BC42319</span><span class="sxs-lookup"><span data-stu-id="2ea2e-106">**Error ID:** BC42319</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2ea2e-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="2ea2e-107">To correct this error</span></span>

<span data-ttu-id="2ea2e-108">Ajoutez l' `cref` attribut à l’exception comme suit :</span><span class="sxs-lookup"><span data-stu-id="2ea2e-108">Add the `cref` attribute to the exception as follows:</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a><span data-ttu-id="2ea2e-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ea2e-109">See also</span></span>

- [\<exception>](../xmldoc/exception.md)
- [<span data-ttu-id="2ea2e-110">Guide pratique : créer une documentation XML</span><span class="sxs-lookup"><span data-stu-id="2ea2e-110">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="2ea2e-111">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="2ea2e-111">XML Comment Tags</span></span>](../xmldoc/index.md)
