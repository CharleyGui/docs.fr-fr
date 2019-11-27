---
title: My.Forms, objet
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: db86704fdc8120ccac5f4489c80a515834ad888f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350371"
---
# <a name="myforms-object"></a>My.Forms, objet

Fournit des propriétés pour accéder à une instance de chaque Windows Form déclaré dans le projet actuel.

## <a name="remarks"></a>Notes

L’objet `My.Forms` fournit une instance de chaque formulaire dans le projet actuel. Le nom de la propriété est le même que celui du formulaire auquel la propriété accède.

Vous pouvez accéder aux formulaires fournis par l’objet `My.Forms` à l’aide du nom du formulaire, sans qualification. Étant donné que le nom de la propriété est le même que le nom du type du formulaire, cela vous permet d’accéder à un formulaire comme s’il avait une instance par défaut. Par exemple, `My.Forms.Form1.Show` équivaut à `Form1.Show`.

L’objet `My.Forms` expose uniquement les formulaires associés au projet actif. Elle ne fournit pas l’accès aux formulaires déclarés dans les dll référencées. Pour accéder à un formulaire fourni par une DLL, vous devez utiliser le nom qualifié du formulaire, écrit sous la forme *DllName*. *NomFormulaire*.

Vous pouvez utiliser la propriété <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> pour obtenir une collection de tous les formulaires ouverts de l’application.

L’objet et ses propriétés sont uniquement disponibles pour les applications Windows.

## <a name="properties"></a>Propriétés

Chaque propriété de l’objet `My.Forms` fournit l’accès à une instance d’un formulaire dans le projet actuel. Le nom de la propriété est le même que celui du formulaire auquel la propriété accède, et le type de propriété est le même que le type du formulaire.

> [!NOTE]
> En cas de collision de nom, le nom de la propriété permettant d’accéder à un formulaire est *RootNamespace*_*namespace*\_*FormName*. Par exemple, considérez deux formulaires nommés `Form1.`si l’un de ces formulaires se trouve dans l’espace de noms racine `WindowsApplication1` et dans l’espace de noms `Namespace1`, vous accéderiez à ce formulaire via `My.Forms.WindowsApplication1_Namespace1_Form1`.

L’objet `My.Forms` permet d’accéder à l’instance du formulaire principal de l’application qui a été créée au démarrage. Pour tous les autres formulaires, l’objet `My.Forms` crée une nouvelle instance du formulaire lors de son accès et le stocke. Les tentatives suivantes d’accès à cette propriété retournent cette instance du formulaire.

Vous pouvez supprimer un formulaire en affectant des `Nothing` à la propriété de ce formulaire. L’accesseur Set de propriété appelle la méthode <xref:System.Windows.Forms.Form.Close%2A> du formulaire, puis affecte `Nothing` à la valeur stockée. Si vous assignez une valeur autre que `Nothing` à la propriété, la méthode setter lève une exception <xref:System.ArgumentException>.

Vous pouvez tester si une propriété de l’objet `My.Forms` stocke une instance du formulaire à l’aide de l’opérateur `Is` ou `IsNot`. Vous pouvez utiliser ces opérateurs pour vérifier si la valeur de la propriété est `Nothing`.

> [!NOTE]
> En règle générale, l’opérateur `Is` ou `IsNot` doit lire la valeur de la propriété pour effectuer la comparaison. Toutefois, si la propriété stocke actuellement `Nothing`, la propriété crée une nouvelle instance du formulaire, puis retourne cette instance. Toutefois, le compilateur Visual Basic traite différemment les propriétés de l’objet `My.Forms` et permet à l’opérateur `Is` ou `IsNot` de vérifier l’état de la propriété sans modifier sa valeur.

## <a name="example"></a>Exemple

Cet exemple modifie le titre du formulaire `SidebarMenu` par défaut.

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

Pour que cet exemple fonctionne, votre projet doit avoir un formulaire nommé `SidebarMenu`.

Ce code ne fonctionne que dans un projet d’application Windows.

## <a name="requirements"></a>Configuration requise

### <a name="availability-by-project-type"></a>Disponibilité par type de projet

|Type de projet|Disponible|
|---|---|
|Application Windows|**Oui**|
|Bibliothèque de classes|Non|
|Application console|Non|
|Bibliothèque de contrôles Windows|Non|
|Bibliothèque de contrôles Web|Non|
|Service Windows|Non|
|Site web|Non|

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [Objets](../../../visual-basic/language-reference/objects/index.md)
- [Is (opérateur)](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot (opérateur)](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Accès aux formulaires de l’application](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
