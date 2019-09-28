---
title: L'exception de commentaire XML doit avoir un attribut 'cref'
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 2e57dc63cb7ad8b2e061296a082d6fa79b464f08
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592037"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a><span data-ttu-id="67bd1-102">L'exception de commentaire XML doit avoir un attribut 'cref'</span><span class="sxs-lookup"><span data-stu-id="67bd1-102">XML comment exception must have a 'cref' attribute</span></span>
<span data-ttu-id="67bd1-103">La balise \<exception > fournit un moyen de documenter les exceptions qui peuvent être levées par une méthode.</span><span class="sxs-lookup"><span data-stu-id="67bd1-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="67bd1-104">L’attribut requis `cref` désigne le nom d’un membre, qui est vérifié par le générateur de documentation.</span><span class="sxs-lookup"><span data-stu-id="67bd1-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="67bd1-105">Si le membre existe, il est traduit en nom d’élément canonique dans le fichier de documentation.</span><span class="sxs-lookup"><span data-stu-id="67bd1-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="67bd1-106">**ID d’erreur :** BC42319</span><span class="sxs-lookup"><span data-stu-id="67bd1-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="67bd1-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="67bd1-107">To correct this error</span></span>  
  
- <span data-ttu-id="67bd1-108">Ajoutez l’attribut `cref` à l’exception comme suit :</span><span class="sxs-lookup"><span data-stu-id="67bd1-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    <span data-ttu-id="67bd1-109">xml</span><span class="sxs-lookup"><span data-stu-id="67bd1-109">xml</span></span>  
    <span data-ttu-id="67bd1-110"><exception cref="member">Description</exception> de' ' '</span><span class="sxs-lookup"><span data-stu-id="67bd1-110">'''<exception cref="member">description</exception></span></span>  
    ```  
  
## See also

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md)
