---
title: L’URI d’espace de noms XML <uri> ne peut être lié qu’à xmlns
ms.date: 07/20/2015
f1_keywords:
- bc31183
- vbc31183
helpviewer_keywords:
- BC31183
ms.assetid: 0ab1dbce-8397-4959-b2cd-f58798b051a0
ms.openlocfilehash: 1aec6ac0a354bfe7e0378a2e46a70a7161bf6d36
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163244"
---
# <a name="bc31183-xml-namespace-uri-httpwwww3orgxml1998namespace-can-be-bound-only-to-xmlns"></a>BC31183 : URI d’espace `http://www.w3.org/XML/1998/namespace` de noms XML ; ne peut être lié qu’à’xmlns'

L’URI `http://www.w3.org/XML/1998/namespace` est utilisé dans une déclaration d’espace de noms XML. Cet URI est un espace de noms réservé et ne peut pas être inclus dans une déclaration d’espace de noms XML.

 **ID d’erreur :** BC31183

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

Supprimez la déclaration d’espace de noms XML ou remplacez l’URI `http://www.w3.org/XML/1998/namespace` par un URI d’espace de noms valide.

## <a name="see-also"></a>Voir aussi

- [Imports, instruction (espace de noms XML)](../statements/imports-statement-xml-namespace.md)
- [Littéraux XML](../xml-literals/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
