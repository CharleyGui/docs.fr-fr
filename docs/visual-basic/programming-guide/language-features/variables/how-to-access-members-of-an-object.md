---
title: "Comment : accéder aux membres d'un objet"
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing
- object variables [Visual Basic], accessing members
ms.assetid: a0072514-6a79-4dd6-8d03-ca8c13e61ddc
ms.openlocfilehash: d44b538e8413eb1412e937375e9bca77600a29b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348667"
---
# <a name="how-to-access-members-of-an-object-visual-basic"></a>Comment : accéder aux membres d'un objet (Visual Basic)

Quand vous avez une variable objet qui fait référence à un objet, vous souhaitez souvent travailler avec les membres de cet objet, tels que ses méthodes, propriétés, champs et événements. Par exemple, une fois que vous avez créé un objet <xref:System.Windows.Forms.Form>, vous souhaiterez peut-être définir sa propriété <xref:System.Windows.Forms.Control.Text%2A> ou appeler sa méthode <xref:System.Windows.Forms.Control.Focus%2A>.

## <a name="accessing-members"></a>Accès aux membres

Vous accédez aux membres d’un objet par le biais de la variable qui y fait référence.

#### <a name="to-access-members-of-an-object"></a>Pour accéder aux membres d’un objet

- Utilisez l’opérateur d’accès aux membres (`.`) entre le nom de la variable objet et le nom du membre.

    ```vb
    currentText = newForm.Text
    ```

    Si le membre est [partagé](../../../../visual-basic/language-reference/modifiers/shared.md), vous n’avez pas besoin d’une variable pour y accéder.

## <a name="accessing-members-of-an-object-of-known-type"></a>Accès aux membres d’un objet de type connu

Si vous connaissez le type d’un objet au moment de la compilation, vous pouvez utiliser la *liaison précoce* pour une variable qui y fait référence.

#### <a name="to-access-members-of-an-object-for-which-you-know-the-type-at-compile-time"></a>Pour accéder aux membres d’un objet pour lequel vous connaissez le type au moment de la compilation

1. Déclarez la variable objet comme étant du type de l’objet que vous souhaitez assigner à la variable.

    ```vb
    Dim extraForm As System.Windows.Forms.Form
    ```

    Avec `Option Strict On`, vous pouvez assigner uniquement des objets <xref:System.Windows.Forms.Form> (ou des objets d’un type dérivé de <xref:System.Windows.Forms.Form>) à `extraForm`. Si vous avez défini une classe ou une structure avec une conversion d' `CType` étendue en <xref:System.Windows.Forms.Form>, vous pouvez également assigner cette classe ou structure à `extraForm`.

2. Utilisez l’opérateur d’accès aux membres (`.`) entre le nom de la variable objet et le nom du membre.

    ```vb
    extraForm.Show()
    ```

    Vous pouvez accéder à toutes les méthodes et propriétés spécifiques à la classe <xref:System.Windows.Forms.Form>, quel que soit le paramètre `Option Strict`.

## <a name="accessing-members-of-an-object-of-unknown-type"></a>Accès aux membres d’un objet de type inconnu

Si vous ne connaissez pas le type d’un objet au moment de la compilation, vous devez utiliser la *liaison tardive* pour toute variable qui y fait référence.

#### <a name="to-access-members-of-an-object-for-which-you-do-not-know-the-type-at-compile-time"></a>Pour accéder aux membres d’un objet pour lequel vous ne connaissez pas le type au moment de la compilation

1. Déclarez la variable objet comme étant du [type de données Object](../../../../visual-basic/language-reference/data-types/object-data-type.md). (Déclarer une variable en tant que `Object` revient à la déclarer comme <xref:System.Object?displayProperty=nameWithType>.)

    ```vb
    Dim someControl As Object
    ```

    Avec `Option Strict On`, vous pouvez accéder uniquement aux membres définis sur la classe <xref:System.Object>.

2. Utilisez l’opérateur d’accès aux membres (`.`) entre le nom de la variable objet et le nom du membre.

    ```vb
    someControl.GetType()
    ```

    Pour pouvoir accéder aux membres de n’importe quel objet que vous affectez à la variable objet, vous devez définir `Option Strict Off`. Dans ce cas, le compilateur ne peut pas garantir qu’un membre donné est exposé par l’objet que vous affectez à la variable. Si l’objet n’expose pas un membre auquel vous essayez d’accéder, une exception <xref:System.MemberAccessException> se produit.

## <a name="see-also"></a>Voir aussi

- <xref:System.Object>
- <xref:System.Windows.Forms.Form>
- <xref:System.MemberAccessException>
- [Variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Déclaration des variables objets](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
