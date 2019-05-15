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
ms.openlocfilehash: 82898e80f5acb2cb0dcab65390701efc8d48115b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586564"
---
# <a name="how-to-enumerate-time-zones-present-on-a-computer"></a>Procédure : énumérer les fuseaux horaires d’un ordinateur

Pour utiliser correctement un fuseau horaire désigné, le système doit pouvoir accéder aux informations le concernant. Les systèmes d’exploitation Windows XP et Windows Vista stocker ces informations dans le Registre. Il existe de nombreux fuseaux horaires dans le monde, mais le Registre contient des informations sur un sous-ensemble de ces fuseaux horaires uniquement. De plus, le Registre est une structure dynamique dont le contenu peut être modifié délibérément ou accidentellement. Par conséquent, une application ne peut pas toujours supposer qu’un fuseau horaire particulier est défini et disponible sur un système. Pour de nombreuses applications qui utilisent des informations de fuseau horaire, il convient en premier lieu de déterminer si les fuseaux horaires requis sont disponibles sur le système local ou de fournir à l’utilisateur la liste des fuseaux horaires qu’il peut sélectionner. Il faut donc qu’une application énumère les fuseaux horaires définis sur un système local.

> [!NOTE]
> Si une application s’appuie sur la présence d’un fuseau horaire particulier qui ne peut pas être définie sur un système local, l’application peut garantir sa présence à sérialiser et désérialiser des informations sur le fuseau horaire. Le fuseau horaire peuvent ensuite être ajouté à un contrôle de liste afin que l’utilisateur de l’application permettre le sélectionner. Pour plus d’informations, consultez [Guide pratique pour Enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) et [Comment : Restaurer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

### <a name="to-enumerate-the-time-zones-present-on-the-local-system"></a>Pour énumérer les fuseaux horaires présents sur le système local

1. Appelez la méthode <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType>. La méthode retourne une collection générique <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection de <xref:System.TimeZoneInfo> objets. Les entrées dans la collection sont triées par leur <xref:System.TimeZoneInfo.DisplayName%2A> propriété. Exemple :

   [!code-csharp[System.TimeZone2.Concepts#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#1)]
   [!code-vb[System.TimeZone2.Concepts#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#1)]

2. Énumérer l’individu <xref:System.TimeZoneInfo> objets dans la collection en utilisant un `foreach` boucle (en c#) ou un `For Each`...`Next` boucle (en Visual Basic) et effectuer tout traitement nécessaire sur chaque objet. Par exemple, le code suivant énumère les <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection de <xref:System.TimeZoneInfo> objets retournée à l’étape 1 et répertorie le nom complet de chaque fuseau horaire sur la console.

   [!code-csharp[System.TimeZone2.Concepts#12](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#12)]
   [!code-vb[System.TimeZone2.Concepts#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#12)]

### <a name="to-present-the-user-with-a-list-of-time-zones-present-on-the-local-system"></a>À l’utilisateur avec une liste des fuseaux horaires présents sur le système local

1. Appelez la méthode <xref:System.TimeZoneInfo.GetSystemTimeZones%2A?displayProperty=nameWithType>. La méthode retourne une collection générique <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> collection de <xref:System.TimeZoneInfo> objets.

2. Assignez la collection retournée à l’étape 1 pour le `DataSource` propriété d’un Windows forms ou ASP.NET contrôle list.

3. Récupérer le <xref:System.TimeZoneInfo> objet que l’utilisateur a sélectionnée.

L’exemple fournit une illustration pour une application Windows.

## <a name="example"></a>Exemple

L’exemple démarre une application Windows qui affiche les fuseaux horaires définis sur un système situé dans une zone de liste. L’exemple affiche ensuite une boîte de dialogue qui contient la valeur de la <xref:System.TimeZoneInfo.DisplayName%2A> propriété de l’objet de fuseau horaire sélectionné par l’utilisateur.

[!code-csharp[System.TimeZone2.Concepts#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#2)]
[!code-vb[System.TimeZone2.Concepts#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#2)]

Plus les contrôles de liste (telles que la <xref:System.Windows.Forms.ListBox?displayProperty=nameWithType> ou <xref:System.Web.UI.WebControls.BulletedList?displayProperty=nameWithType> contrôle) vous permettent d’assigner une collection de variables objet à leur `DataSource` propriété tant que cette collection implémente le <xref:System.Collections.IEnumerable> interface. (Le générique <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> classe.) Pour afficher un objet individuel dans la collection, le contrôle appelle l’objet `ToString` méthode pour extraire la chaîne qui est utilisée pour représenter l’objet. Dans le cas de <xref:System.TimeZoneInfo> objets, le `ToString` méthode retourne le <xref:System.TimeZoneInfo> nom d’affichage de l’objet (la valeur de son <xref:System.TimeZoneInfo.DisplayName%2A> propriété).

> [!NOTE]
> Étant donné que les contrôles de liste appellent d’un objet `ToString` (méthode), vous pouvez assigner une collection de <xref:System.TimeZoneInfo> objets au contrôle, que le contrôle soit afficher un nom explicite pour chaque objet et récupérer le <xref:System.TimeZoneInfo> objet que l’utilisateur a sélectionnée. Cela vous évite de devoir extraire une chaîne pour chaque objet dans la collection, affectez la chaîne à une collection qui est assignée à son tour du contrôle `DataSource` propriété, récupérez la chaîne de l’utilisateur a sélectionné et ensuite utiliser cette chaîne pour extraire l’objet qu’il décrit. 

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

* Que les espaces de noms suivants soient importés :

  <xref:System> (en c#)

  <xref:System.Collections.ObjectModel>

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
- [Guide pratique pour Enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
- [Guide pratique pour Restaurer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
