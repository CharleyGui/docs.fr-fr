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
ms.openlocfilehash: cd2119d6d22f3f676b7167ed545aeb058123cfb5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122201"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>Procédure : restaurer des fuseaux horaires à partir d’une ressource incorporée

Cette rubrique explique comment restaurer des fuseaux horaires qui ont été enregistrés dans un fichier de ressources. Pour obtenir des informations et des instructions sur l’enregistrement des fuseaux horaires, consultez [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>Pour désérialiser un objet TimeZoneInfo à partir d’une ressource incorporée

1. Si le fuseau horaire à récupérer n’est pas un fuseau horaire personnalisé, essayez de l’instancier à l’aide de la méthode <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>.

2. Instanciez un objet <xref:System.Resources.ResourceManager> en passant le nom qualifié complet du fichier de ressources incorporé et une référence à l’assembly qui contient le fichier de ressources.

   Si vous ne pouvez pas déterminer le nom complet du fichier de ressources incorporé, utilisez [Ildasm. exe (Désassembleur il)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) pour examiner le manifeste de l’assembly. Une entrée de `.mresource` identifie la ressource. Dans l’exemple, le nom complet de la ressource est `SerializeTimeZoneData.SerializedTimeZones`.

   Si le fichier de ressources est incorporé dans le même assembly qui contient le code d’instanciation de fuseau horaire, vous pouvez récupérer une référence à ce dernier en appelant la méthode de <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> `static` (`Shared` dans Visual Basic).

3. Si l’appel à la méthode <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> échoue ou si un fuseau horaire personnalisé doit être instancié, récupérez une chaîne qui contient le fuseau horaire sérialisé en appelant la méthode <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>.

4. Désérialisez les données de fuseau horaire en appelant la méthode <xref:System.TimeZoneInfo.FromSerializedString%2A>.

## <a name="example"></a>Exemple

L’exemple suivant désérialise un objet <xref:System.TimeZoneInfo> stocké dans un fichier de ressources .NET XML incorporé.

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

Ce code illustre la gestion des exceptions pour s’assurer qu’un objet <xref:System.TimeZoneInfo> requis par l’application est présent. Il tente d’abord d’instancier un objet <xref:System.TimeZoneInfo> en le récupérant à partir du Registre à l’aide de la méthode <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A>. Si le fuseau horaire ne peut pas être instancié, le code le récupère à partir du fichier de ressources incorporé.

Étant donné que les données des fuseaux horaires personnalisés (fuseaux horaires instanciés à l’aide de la méthode <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A>) ne sont pas stockées dans le registre, le code n’appelle pas la <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> pour instancier le fuseau horaire de Palmer, Antarctique. Au lieu de cela, il consulte immédiatement le fichier de ressources incorporé pour récupérer une chaîne qui contient les données du fuseau horaire avant d’appeler la méthode <xref:System.TimeZoneInfo.FromSerializedString%2A>.

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- Qu’une référence à System. Windows. Forms. dll et System. Core. dll soit ajoutée au projet.

- Que les espaces de noms suivants soient importés :

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
- [Vue d’ensemble des fuseaux horaires](../../../docs/standard/datetime/time-zone-overview.md)
- [Guide pratique pour enregistrer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
