---
title: Vérification des noms d'attribut et d'élément XML lors de la création de nœuds
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
ms.openlocfilehash: 7c99ffa9d139d94d26c562cb1668f1b855bed32d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709944"
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="dba19-102">Vérification des noms d'attribut et d'élément XML lors de la création de nœuds</span><span class="sxs-lookup"><span data-stu-id="dba19-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="dba19-103">Le DOM (Document Object Model) XML contrôle la validité des noms lors de la création de nœuds d'élément ou d'attribut.</span><span class="sxs-lookup"><span data-stu-id="dba19-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="dba19-104">Si ces noms contiennent des caractères non conformes, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="dba19-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="dba19-105">Pour être certain que les noms sont valides et encodés correctement, vous devez recourir à la classe **XmlConvert** pour encoder le nom et le décoder à nouveau au niveau de l'application.</span><span class="sxs-lookup"><span data-stu-id="dba19-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="dba19-106">**XmlWriter** possède des méthodes qui effectuent des opérations supplémentaires afin de garantir un format correct pour le code XML qui est généré.</span><span class="sxs-lookup"><span data-stu-id="dba19-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba19-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dba19-107">See also</span></span>

- [<span data-ttu-id="dba19-108">DOM (Document Object Model) XML</span><span class="sxs-lookup"><span data-stu-id="dba19-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
