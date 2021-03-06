---
title: <interfacename><membername> est déjà implémenté par la classe de base <baseclassname>. Réimplémentation de <type> attendue
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 8137f6b1712b6a0752a991f5a3d598b5f958252c
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162815"
---
# <a name="bc42015-interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a>BC42015 : ' \<interfacename> . \<membername> 'est déjà implémenté par la classe de base' \<baseclassname> '. Réimplémentation de \<type> attendue

Une propriété, une procédure ou un événement dans une classe dérivée utilise une `Implements` clause qui spécifie un membre d’interface qui est déjà implémenté dans la classe de base.

 Une classe dérivée peut réimplémenter un membre d’interface qui est implémenté par sa classe de base. La substitution de l’implémentation de la classe de base est une procédure différente. Pour plus d’informations, consultez [Implements](../statements/implements-clause.md).

 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **ID d’erreur :** BC42015

## <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Si vous comptez réimplémenter le membre d’interface, aucune mesure n’est nécessaire. Le code de votre classe dérivée accède au membre réimplémenté, sauf si vous utilisez le `MyBase` mot clé pour accéder à l’implémentation de la classe de base.

- Si vous ne comptez pas réimplémenter le membre d’interface, supprimez la clause `Implements` de la déclaration de la propriété, de la procédure ou de l’événement.

## <a name="see-also"></a>Voir aussi

- [Interfaces](../../programming-guide/language-features/interfaces/index.md)
