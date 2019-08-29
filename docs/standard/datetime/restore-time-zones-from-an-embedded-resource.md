---
title: 'Procédure : restaurer des fuseaux horaires à partir d’une ressource incorporée'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98813bf6685be78d33ebd5cc5e8c07a61a811c25
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106749"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>Procédure : restaurer des fuseaux horaires à partir d’une ressource incorporée

Cette rubrique explique comment restaurer des fuseaux horaires qui ont été enregistrés dans un fichier de ressources. Pour obtenir des informations et des instructions sur l’enregistrement [des fuseaux horaires, consultez Procédure: Enregistrer des fuseaux horaires dans une](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)ressource incorporée.

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>Pour désérialiser un objet TimeZoneInfo à partir d’une ressource incorporée

1. Si le fuseau horaire à récupérer n’est pas un fuseau horaire personnalisé, essayez de l’instancier à l' <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> aide de la méthode.

2. Instanciez <xref:System.Resources.ResourceManager> un objet en passant le nom qualifié complet du fichier de ressources incorporé et une référence à l’assembly qui contient le fichier de ressources.

   Si vous ne pouvez pas déterminer le nom complet du fichier de ressources incorporé, utilisez [Ildasm. exe (Désassembleur il)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pour examiner le manifeste de l’assembly. Une `.mresource` entrée identifie la ressource. Dans l’exemple, le nom complet de la ressource est `SerializeTimeZoneData.SerializedTimeZones`.

   Si le fichier de ressources est incorporé dans le même assembly qui contient le code d’instanciation du fuseau horaire, vous pouvez récupérer une `static` référence`Shared` à celui- <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> ci en appelant la méthode (en Visual Basic).

3. Si l’appel à la <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> méthode échoue, ou si un fuseau horaire personnalisé doit être instancié, récupérez une chaîne qui contient le fuseau horaire sérialisé en appelant la <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> méthode.

4. Désérialisez les données de fuseau horaire en appelant <xref:System.TimeZoneInfo.FromSerializedString%2A> la méthode.

## <a name="example"></a>Exemple

L’exemple suivant désérialise un <xref:System.TimeZoneInfo> objet stocké dans un fichier de ressources XML .net incorporé.

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

Ce code illustre la gestion des exceptions pour s’assurer <xref:System.TimeZoneInfo> qu’un objet requis par l’application est présent. Il tente d’abord d’instancier un <xref:System.TimeZoneInfo> objet en le récupérant à partir du Registre à l’aide de la <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> méthode. Si le fuseau horaire ne peut pas être instancié, le code le récupère à partir du fichier de ressources incorporé.

Étant donné que les données des fuseaux horaires personnalisés (fuseaux horaires <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> instanciés à l’aide de la méthode) ne sont pas stockées dans le <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> Registre, le code n’appelle pas pour instancier le fuseau horaire pour Palmer, Antarctique. Au lieu de cela, il consulte immédiatement le fichier de ressources incorporé pour récupérer une chaîne qui contient les données du fuseau <xref:System.TimeZoneInfo.FromSerializedString%2A> horaire avant d’appeler la méthode.

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- Qu’une référence à System. Windows. Forms. dll et System. Core. dll soit ajoutée au projet.

- Que les espaces de noms suivants soient importés:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
- [Vue d’ensemble des fuseaux horaires](../../../docs/standard/datetime/time-zone-overview.md)
- [Guide pratique pour Enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
