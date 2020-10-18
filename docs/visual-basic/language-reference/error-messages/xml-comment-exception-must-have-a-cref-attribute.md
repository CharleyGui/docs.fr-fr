---
title: L'exception de commentaire XML doit avoir un attribut 'cref'
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 18e7aa5f6905eaa9c509aa21fe6f5bfcd54d46f0
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163296"
---
# <a name="bc42319-xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="e1c86-102">BC42319 : l’exception de commentaire XML doit avoir un attribut’CREF'</span><span class="sxs-lookup"><span data-stu-id="e1c86-102">BC42319: XML comment exception must have a 'cref' attribute</span></span>

<span data-ttu-id="e1c86-103">La \<exception> balise permet de documenter les exceptions qui peuvent être levées par une méthode.</span><span class="sxs-lookup"><span data-stu-id="e1c86-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="e1c86-104">L’attribut required `cref` désigne le nom d’un membre, qui est vérifié par le générateur de documentation.</span><span class="sxs-lookup"><span data-stu-id="e1c86-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="e1c86-105">Si le membre existe, il est traduit en nom d’élément canonique dans le fichier de documentation.</span><span class="sxs-lookup"><span data-stu-id="e1c86-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>

<span data-ttu-id="e1c86-106">**ID d’erreur :** BC42319</span><span class="sxs-lookup"><span data-stu-id="e1c86-106">**Error ID:** BC42319</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e1c86-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="e1c86-107">To correct this error</span></span>

<span data-ttu-id="e1c86-108">Ajoutez l' `cref` attribut à l’exception comme suit :</span><span class="sxs-lookup"><span data-stu-id="e1c86-108">Add the `cref` attribute to the exception as follows:</span></span>

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a><span data-ttu-id="e1c86-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1c86-109">See also</span></span>

- [\<exception>](../xmldoc/exception.md)
- [<span data-ttu-id="e1c86-110">Guide pratique : créer une documentation XML</span><span class="sxs-lookup"><span data-stu-id="e1c86-110">How to: Create XML Documentation</span></span>](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="e1c86-111">Étiquettes XML pour les commentaires</span><span class="sxs-lookup"><span data-stu-id="e1c86-111">XML Comment Tags</span></span>](../xmldoc/index.md)
