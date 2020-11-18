---
title: 'Procédure : restaurer des fuseaux horaires à partir d’une ressource incorporée'
ms.date: 04/10/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET], deserializing
- time zones [.NET], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
ms.openlocfilehash: a1302f595a0907103bae2695e703e5af6da660a7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817664"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>Procédure : restaurer des fuseaux horaires à partir d’une ressource incorporée

Cette rubrique explique comment restaurer des fuseaux horaires qui ont été enregistrés dans un fichier de ressources. Pour obtenir des informations et des instructions sur l’enregistrement des fuseaux horaires, consultez [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](save-time-zones-to-an-embedded-resource.md).

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>Pour désérialiser un objet TimeZoneInfo à partir d’une ressource incorporée

1. Si le fuseau horaire à récupérer n’est pas un fuseau horaire personnalisé, essayez de l’instancier à l’aide de la <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> méthode.

2. Instanciez un <xref:System.Resources.ResourceManager> objet en passant le nom qualifié complet du fichier de ressources incorporé et une référence à l’assembly qui contient le fichier de ressources.

   Si vous ne pouvez pas déterminer le nom complet du fichier de ressources incorporé, utilisez le [Ildasm.exe (Désassembleur il)](../../framework/tools/ildasm-exe-il-disassembler.md) pour examiner le manifeste de l’assembly. Une `.mresource` entrée identifie la ressource. Dans l’exemple, le nom complet de la ressource est `SerializeTimeZoneData.SerializedTimeZones` .

   Si le fichier de ressources est incorporé dans le même assembly qui contient le code d’instanciation du fuseau horaire, vous pouvez récupérer une référence à celui-ci en appelant la `static` `Shared` méthode (en Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> .

3. Si l’appel à la <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> méthode échoue, ou si un fuseau horaire personnalisé doit être instancié, récupérez une chaîne qui contient le fuseau horaire sérialisé en appelant la <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> méthode.

4. Désérialisez les données de fuseau horaire en appelant la <xref:System.TimeZoneInfo.FromSerializedString%2A> méthode.

## <a name="example"></a>Exemple

L’exemple suivant désérialise un <xref:System.TimeZoneInfo> objet stocké dans un fichier de ressources XML .net incorporé.

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

Ce code illustre la gestion des exceptions pour s’assurer qu’un <xref:System.TimeZoneInfo> objet requis par l’application est présent. Il tente d’abord d’instancier un <xref:System.TimeZoneInfo> objet en le récupérant à partir du Registre à l’aide de la <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> méthode. Si le fuseau horaire ne peut pas être instancié, le code le récupère à partir du fichier de ressources incorporé.

Étant donné que les données des fuseaux horaires personnalisés (fuseaux horaires instanciés à l’aide de la <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> méthode) ne sont pas stockées dans le registre, le code n’appelle pas <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> pour instancier le fuseau horaire pour Palmer, Antarctique. Au lieu de cela, il consulte immédiatement le fichier de ressources incorporé pour récupérer une chaîne qui contient les données du fuseau horaire avant d’appeler la <xref:System.TimeZoneInfo.FromSerializedString%2A> méthode.

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- Qu’une référence à System.Windows.Forms.dll et System.Core.dll être ajoutée au projet.

- Que les espaces de noms suivants soient importés :

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](index.md)
- [Vue d’ensemble des fuseaux horaires](time-zone-overview.md)
- [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](save-time-zones-to-an-embedded-resource.md)
