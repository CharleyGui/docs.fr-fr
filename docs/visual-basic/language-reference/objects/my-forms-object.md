---
title: My.Forms, objet
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 001f6fbfae2467ea0af5e98ca041b694d1e7b8f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372438"
---
# <a name="myforms-object"></a>My.Forms, objet

Fournit des propriétés pour accéder à une instance de chaque Windows Form déclaré dans le projet actuel.

## <a name="remarks"></a>Notes

L' `My.Forms` objet fournit une instance de chaque formulaire dans le projet actuel. Le nom de la propriété est le même que celui du formulaire auquel la propriété accède.

Vous pouvez accéder aux formulaires fournis par l' `My.Forms` objet à l’aide du nom du formulaire, sans qualification. Étant donné que le nom de la propriété est le même que le nom du type du formulaire, cela vous permet d’accéder à un formulaire comme s’il avait une instance par défaut. Par exemple, `My.Forms.Form1.Show` équivaut à `Form1.Show`.

L' `My.Forms` objet expose uniquement les formulaires associés au projet actif. Elle ne fournit pas l’accès aux formulaires déclarés dans les dll référencées. Pour accéder à un formulaire fourni par une DLL, vous devez utiliser le nom qualifié du formulaire, écrit sous la forme *DllName*. *NomFormulaire*.

Vous pouvez utiliser la <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> propriété pour obtenir une collection de tous les formulaires ouverts de l’application.

L’objet et ses propriétés sont uniquement disponibles pour les applications Windows.

## <a name="properties"></a>Propriétés

Chaque propriété de l' `My.Forms` objet permet d’accéder à une instance d’un formulaire dans le projet actuel. Le nom de la propriété est le même que celui du formulaire auquel la propriété accède, et le type de propriété est le même que le type du formulaire.

> [!NOTE]
> En cas de collision de nom, le nom de la propriété permettant d’accéder à un formulaire est *RootNamespace*_*namespace* \_ *NomFormulaire*. Par exemple, considérez deux formulaires nommés `Form1.` si l’un de ces formulaires se trouve dans l’espace de noms racine `WindowsApplication1` et dans l’espace de noms `Namespace1` , vous accéderiez à ce formulaire via `My.Forms.WindowsApplication1_Namespace1_Form1` .

L' `My.Forms` objet fournit l’accès à l’instance du formulaire principal de l’application qui a été créée au démarrage. Pour tous les autres formulaires, l' `My.Forms` objet crée une nouvelle instance du formulaire lors de son accès et le stocke. Les tentatives suivantes d’accès à cette propriété retournent cette instance du formulaire.

Vous pouvez supprimer un formulaire en l’affectant `Nothing` à la propriété de ce formulaire. L’accesseur Set de propriété appelle la <xref:System.Windows.Forms.Form.Close%2A> méthode du formulaire, puis assigne `Nothing` à la valeur stockée. Si vous assignez une valeur autre que `Nothing` à la propriété, la méthode setter lève une <xref:System.ArgumentException> exception.

Vous pouvez tester si une propriété de l' `My.Forms` objet stocke une instance du formulaire à l’aide de l' `Is` `IsNot` opérateur or. Vous pouvez utiliser ces opérateurs pour vérifier si la valeur de la propriété est `Nothing` .

> [!NOTE]
> En règle générale, l' `Is` `IsNot` opérateur or doit lire la valeur de la propriété pour effectuer la comparaison. Toutefois, si la propriété est actuellement stockée `Nothing` , la propriété crée une nouvelle instance du formulaire, puis retourne cette instance. Toutefois, le compilateur Visual Basic traite différemment les propriétés de l' `My.Forms` objet et permet `Is` à l' `IsNot` opérateur ou de vérifier l’état de la propriété sans modifier sa valeur.

## <a name="example"></a>Exemple

Cet exemple modifie le titre du formulaire par défaut `SidebarMenu` .

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

Pour que cet exemple fonctionne, votre projet doit avoir un formulaire nommé `SidebarMenu` .

Ce code ne fonctionne que dans un projet d’application Windows.

## <a name="requirements"></a>Spécifications

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
- [Objets](index.md)
- [Is, opérateur](../operators/is-operator.md)
- [IsNot, opérateur](../operators/isnot-operator.md)
- [Accès aux formulaires d’application](../../developing-apps/programming/accessing-application-forms.md)
