---
title: 'Procédure : énumérer les fuseaux horaires d’un ordinateur'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], enumerating
- enumerating time zones [.NET Framework]
ms.assetid: bb7a42ab-6bd9-4c5c-b734-5546d51f8669
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afc3b57659dd6719f72cefba8a6d2f1abe08c0d0
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106649"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Procédure : énumérer les fuseaux horaires d’un ordinateur

Pour utiliser correctement un fuseau horaire désigné, le système doit pouvoir accéder aux informations le concernant. Les systèmes d’exploitation Windows XP et Windows Vista stockent ces informations dans le registre. Il existe de nombreux fuseaux horaires dans le monde, mais le Registre contient des informations sur un sous-ensemble de ces fuseaux horaires uniquement. De plus, le Registre est une structure dynamique dont le contenu peut être modifié délibérément ou accidentellement. Par conséquent, une application ne peut pas toujours supposer qu’un fuseau horaire particulier est défini et disponible sur un système. Pour de nombreuses applications qui utilisent des informations de fuseau horaire, il convient en premier lieu de déterminer si les fuseaux horaires requis sont disponibles sur le système local ou de fournir à l’utilisateur la liste des fuseaux horaires qu’il peut sélectionner. Il faut donc qu’une application énumère les fuseaux horaires définis sur un système local.

> [!NOTE]
> Si une application s’appuie sur la présence d’un fuseau horaire particulier qui ne peut pas être défini sur un système local, l’application peut garantir sa présence en sérialisant et désérialiser des informations sur le fuseau horaire. Le fuseau horaire peut ensuite être ajouté à un contrôle de liste afin que l’utilisateur de l’application puisse le sélectionner. Pour plus d’informations, consultez [Guide pratique pour Enregistrez les fuseaux horaires dans une](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) ressource [incorporée et comment: Restaurer des fuseaux horaires à partir](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)d’une ressource incorporée.

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>Pour énumérer les fuseaux horaires présents sur le système local

1. Appelez la méthode <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType>. La méthode retourne une collection <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> générique d' <xref:System.TimeZoneInfo> objets. Les entrées de la collection sont triées en <xref:System.TimeZoneInfo.DisplayName%2A> fonction de leur propriété. Exemple :

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. Énumérer les objets <xref:System.TimeZoneInfo> individuels dans la collection à l’aide `foreach` d’une boucle C#(dans) `For Each`ou d’un...`Next` Loop (en Visual Basic) et effectue le traitement nécessaire sur chaque objet. Par exemple, le code suivant énumère la <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection d' <xref:System.TimeZoneInfo> objets retournée à l’étape 1 et répertorie le nom complet de chaque fuseau horaire sur la console.

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>Pour présenter à l’utilisateur une liste des fuseaux horaires présents sur le système local

1. Appelez la méthode <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType>. La méthode retourne une collection <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> générique d' <xref:System.TimeZoneInfo> objets.

2. Assignez la collection retournée à l' `DataSource` étape 1 à la propriété d’un contrôle de liste Windows Forms ou ASP.net.

3. Récupérez <xref:System.TimeZoneInfo> l’objet sélectionné par l’utilisateur.

L’exemple fournit une illustration pour une application Windows.

## <a name="example"></a>Exemple

L’exemple démarre une application Windows qui affiche les fuseaux horaires définis sur un système dans une zone de liste. L’exemple affiche ensuite une boîte de dialogue qui contient la valeur de <xref:System.TimeZoneInfo.DisplayName%2A> la propriété de l’objet de fuseau horaire sélectionné par l’utilisateur.

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

La plupart des contrôles de liste ( <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> tels <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> que le contrôle ou) vous permettent d’assigner une collection `DataSource` de variables objet à leur propriété à condition que <xref:System.Collections.IEnumerable> cette collection implémente l’interface. (C’est <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> le cas de la classe générique.) Pour afficher un objet individuel dans la collection, le contrôle appelle la méthode de `ToString` cet objet pour extraire la chaîne utilisée pour représenter l’objet. Dans le cas d' <xref:System.TimeZoneInfo> objets, la `ToString` méthode retourne le <xref:System.TimeZoneInfo> nom complet de l’objet (la valeur de <xref:System.TimeZoneInfo.DisplayName%2A> sa propriété).

> [!NOTE]
> Étant donné que les contrôles de liste `ToString` appellent la méthode d’un objet, vous <xref:System.TimeZoneInfo> pouvez assigner une collection d’objets au contrôle, faire en sorte que le contrôle affiche un <xref:System.TimeZoneInfo> nom explicite pour chaque objet et récupérer l’objet sélectionné par l’utilisateur. Cela élimine le besoin d’extraire une chaîne pour chaque objet de la collection, d’assigner la chaîne à une collection qui est à son tour affectée `DataSource` à la propriété du contrôle, de récupérer la chaîne sélectionnée par l’utilisateur, puis d’utiliser cette chaîne pour extraire l’objet. qu’il décrit. 

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- Que les espaces de noms suivants soient importés:

  <xref:System>(dans C# le code)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
- [Guide pratique pour Enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
- [Guide pratique pour Restaurer des fuseaux horaires à partir d’une ressource incorporée](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
