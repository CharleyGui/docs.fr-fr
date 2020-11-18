---
title: 'Procédure : énumérer les fuseaux horaires d’un ordinateur'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], enumerating
- enumerating time zones [.NET]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
ms.openlocfilehash: 276c13bb95685e9588e25238f1a6e45cd57a6c91
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817963"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Procédure : énumérer les fuseaux horaires d’un ordinateur

Pour utiliser correctement un fuseau horaire désigné, le système doit pouvoir accéder aux informations le concernant. Les systèmes d’exploitation Windows XP et Windows Vista stockent ces informations dans le registre. Il existe de nombreux fuseaux horaires dans le monde, mais le Registre contient des informations sur un sous-ensemble de ces fuseaux horaires uniquement. De plus, le Registre est une structure dynamique dont le contenu peut être modifié délibérément ou accidentellement. Par conséquent, une application ne peut pas toujours supposer qu’un fuseau horaire particulier est défini et disponible sur un système. Pour de nombreuses applications qui utilisent des informations de fuseau horaire, il convient en premier lieu de déterminer si les fuseaux horaires requis sont disponibles sur le système local ou de fournir à l’utilisateur la liste des fuseaux horaires qu’il peut sélectionner. Il faut donc qu’une application énumère les fuseaux horaires définis sur un système local.

> [!NOTE]
> Si une application s’appuie sur la présence d’un fuseau horaire particulier qui ne peut pas être défini sur un système local, l’application peut garantir sa présence en sérialisant et désérialiser des informations sur le fuseau horaire. Le fuseau horaire peut ensuite être ajouté à un contrôle de liste afin que l’utilisateur de l’application puisse le sélectionner. Pour plus d’informations, consultez [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](save-time-zones-to-an-embedded-resource.md) et [Comment : restaurer des fuseaux horaires à partir d’une ressource incorporée](restore-time-zones-from-an-embedded-resource.md).

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>Pour énumérer les fuseaux horaires présents sur le système local

1. Appelez la méthode <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> . La méthode retourne une <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection générique d' <xref:System.TimeZoneInfo> objets. Les entrées de la collection sont triées en fonction de leur <xref:System.TimeZoneInfo.DisplayName%2A> propriété. Par exemple :

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. Énumérer les <xref:System.TimeZoneInfo> objets individuels dans la collection à l’aide d’une `foreach` boucle (en C#) ou d’un `For Each` ...`Next` Loop (en Visual Basic) et effectue le traitement nécessaire sur chaque objet. Par exemple, le code suivant énumère la <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection d' <xref:System.TimeZoneInfo> objets retournée à l’étape 1 et répertorie le nom complet de chaque fuseau horaire sur la console.

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>Pour présenter à l’utilisateur une liste des fuseaux horaires présents sur le système local

1. Appelez la méthode <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType> . La méthode retourne une <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection générique d' <xref:System.TimeZoneInfo> objets.

2. Assignez la collection retournée à l’étape 1 à la `DataSource` propriété d’un contrôle de liste Windows Forms ou ASP.net.

3. Récupérez l' <xref:System.TimeZoneInfo> objet sélectionné par l’utilisateur.

L’exemple fournit une illustration pour une application Windows.

## <a name="example"></a>Exemple

L’exemple démarre une application Windows qui affiche les fuseaux horaires définis sur un système dans une zone de liste. L’exemple affiche ensuite une boîte de dialogue qui contient la valeur de la <xref:System.TimeZoneInfo.DisplayName%2A> propriété de l’objet de fuseau horaire sélectionné par l’utilisateur.

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

La plupart des contrôles de liste (tels que le <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> contrôle ou) vous permettent d’assigner une collection de variables objet à leur `DataSource` propriété à condition que cette collection implémente l' <xref:System.Collections.IEnumerable> interface. ( <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> C’est le cas de la classe générique.) Pour afficher un objet individuel dans la collection, le contrôle appelle la méthode de cet objet `ToString` pour extraire la chaîne utilisée pour représenter l’objet. Dans le cas d' <xref:System.TimeZoneInfo> objets, la `ToString` méthode retourne le <xref:System.TimeZoneInfo> nom complet de l’objet (la valeur de sa <xref:System.TimeZoneInfo.DisplayName%2A> propriété).

> [!NOTE]
> Étant donné que les contrôles de liste appellent la méthode d’un objet `ToString` , vous pouvez assigner une collection d' <xref:System.TimeZoneInfo> objets au contrôle, faire en sorte que le contrôle affiche un nom explicite pour chaque objet et récupérer l' <xref:System.TimeZoneInfo> objet sélectionné par l’utilisateur. Cela élimine le besoin d’extraire une chaîne pour chaque objet de la collection, d’assigner la chaîne à une collection qui est à son tour affectée à la propriété du contrôle `DataSource` , de récupérer la chaîne sélectionnée par l’utilisateur, puis d’utiliser cette chaîne pour extraire l’objet qu’elle décrit.

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- Que les espaces de noms suivants soient importés :

  <xref:System> (dans le code C#)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](index.md)
- [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](save-time-zones-to-an-embedded-resource.md)
- [Procédure : restaurer des fuseaux horaires à partir d’une ressource incorporée](restore-time-zones-from-an-embedded-resource.md)
