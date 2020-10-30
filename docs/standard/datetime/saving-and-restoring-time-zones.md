---
title: Enregistrement et restauration de fuseaux horaires
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- restoring time zones
- deserialization [.NET], time zones
- serialization [.NET], time zones
- time zone objects [.NET], restoring
- saving time zones
- time zone objects [.NET], deserializing
- time zones [.NET], saving
- time zones [.NET], restoring
- time zone objects [.NET], serializing
- time zone objects [.NET], saving
ms.assetid: 4028b310-e7ce-49d4-a646-1e83bfaf6f9d
ms.openlocfilehash: 6a05bf4ce062a3f4e539e9b89779cb468b9782a6
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063389"
---
# <a name="saving-and-restoring-time-zones"></a>Enregistrement et restauration de fuseaux horaires

La <xref:System.TimeZoneInfo> classe s’appuie sur le registre pour récupérer des données de fuseau horaire prédéfinies. Toutefois, le Registre est une structure dynamique. En outre, les informations de fuseau horaire contenues dans le Registre sont utilisées par le système d’exploitation principalement pour gérer les ajustements et les conversions de temps pour l’année en cours. Cela a deux implications majeures pour les applications qui reposent sur des données de fuseau horaire précises :

- Un fuseau horaire requis par une application ne peut pas être défini dans le registre, ou il a peut-être été renommé ou supprimé du Registre.

- Un fuseau horaire défini dans le registre peut ne pas avoir d’informations sur les règles d’ajustement particulières nécessaires à l’historique des conversions de fuseau horaire.

La <xref:System.TimeZoneInfo> classe répond à ces limitations par le biais de sa prise en charge de la sérialisation (enregistrement) et de la désérialisation (restauration) des données de fuseau horaire.

## <a name="time-zone-serialization-and-deserialization"></a>Sérialisation et désérialisation des fuseaux horaires

L’enregistrement et la restauration d’un fuseau horaire par la sérialisation et la désérialisation des données de fuseau horaire impliquent uniquement deux appels de méthode :

- Vous pouvez sérialiser un <xref:System.TimeZoneInfo> objet en appelant la méthode de cet objet <xref:System.TimeZoneInfo.ToSerializedString%2A> . La méthode n’accepte aucun paramètre et retourne une chaîne qui contient des informations de fuseau horaire.

- Vous pouvez désérialiser un <xref:System.TimeZoneInfo> objet à partir d’une chaîne sérialisée en passant cette chaîne à la `static` `Shared` méthode (dans Visual Basic) <xref:System.TimeZoneInfo.FromSerializedString%2A?displayProperty=nameWithType> .

## <a name="serialization-and-deserialization-scenarios"></a>Scénarios de sérialisation et de désérialisation

La possibilité d’enregistrer (ou de sérialiser) un <xref:System.TimeZoneInfo> objet dans une chaîne et de le restaurer (ou de le désérialiser) pour une utilisation ultérieure augmente à la fois l’utilitaire et la flexibilité de la <xref:System.TimeZoneInfo> classe. Cette section examine certaines situations dans lesquelles la sérialisation et la désérialisation sont particulièrement utiles.

### <a name="serializing-and-deserializing-time-zone-data-in-an-application"></a>Sérialisation et désérialisation des données de fuseau horaire dans une application

Un fuseau horaire sérialisé peut être restauré à partir d’une chaîne lorsqu’il est nécessaire. Une application peut effectuer cette opération si le fuseau horaire récupéré à partir du registre ne parvient pas à convertir correctement une date et une heure dans une plage de dates particulière. Par exemple, les données de fuseau horaire dans le Registre Windows XP prennent en charge une seule règle d’ajustement, tandis que les fuseaux horaires définis dans le Registre Windows Vista fournissent généralement des informations sur deux règles d’ajustement. Cela signifie que les conversions d’heure historiques peuvent être inexactes. La sérialisation et la désérialisation des données de fuseau horaire peuvent gérer cette limitation.

Dans l’exemple suivant, une <xref:System.TimeZoneInfo> classe personnalisée qui n’a pas de règles d’ajustement est définie pour représenter le fuseau horaire des États-Unis de l’est de 1883 à 1917, avant l’introduction de l’heure d’été dans la États-Unis. Le fuseau horaire personnalisé est sérialisé dans une variable qui a une portée globale. La méthode de conversion de fuseau horaire, `ConvertUtcTime` , est passée au temps universel coordonné (UTC, Coordinated Universal Time) à convertir. Si la date et l’heure se produisent dans 1917 ou une version antérieure, le fuseau horaire de l’est personnalisé est restauré à partir d’une chaîne sérialisée et remplace le fuseau horaire récupéré dans le registre.

[!code-csharp[System.TimeZone2.Serialization.1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/cs/Serialization.cs#1)]
[!code-vb[System.TimeZone2.Serialization.1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.1/vb/Serialization.vb#1)]

### <a name="handling-time-zone-exceptions"></a>Gestion des exceptions de fuseau horaire

Étant donné que le Registre est une structure dynamique, son contenu est soumis à une modification accidentelle ou intentionnelle. Cela signifie qu’un fuseau horaire qui doit être défini dans le registre et qu’il est nécessaire pour qu’une application s’exécute correctement peut être absent. Sans prise en charge de la sérialisation et de la désérialisation des fuseaux horaires, vous avez peu de choix, mais pour gérer le résultant <xref:System.TimeZoneNotFoundException> en mettant fin à l’application. Toutefois, en utilisant la sérialisation et la désérialisation des fuseaux horaires, vous pouvez gérer un inattendu <xref:System.TimeZoneNotFoundException> en restaurant le fuseau horaire requis à partir d’une chaîne sérialisée, et l’application continue de s’exécuter.

L’exemple suivant crée et sérialise un fuseau horaire standard personnalisé. Il essaie ensuite de récupérer le fuseau horaire central à partir du Registre. Si l’opération de récupération lève une <xref:System.TimeZoneNotFoundException> <xref:System.InvalidTimeZoneException> exception ou, le gestionnaire d’exceptions désérialise le fuseau horaire.

[!code-csharp[System.TimeZone2.Serialization.2#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/cs/Serialization2.cs#1)]
[!code-vb[System.TimeZone2.Serialization.2#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Serialization.2/vb/Serialization2.vb#1)]

### <a name="storing-a-serialized-string-and-restoring-it-when-needed"></a>Stockage d’une chaîne sérialisée et restauration en cas de besoin

Les exemples précédents comportent des informations de fuseau horaire stockées dans une variable de chaîne et les ont restaurées si nécessaire. Toutefois, la chaîne qui contient les informations de fuseau horaire sérialisées peut elle-même être stockée dans un support de stockage, tel qu’un fichier externe, un fichier de ressources incorporé dans l’application ou le registre. (Notez que les informations sur les fuseaux horaires personnalisés doivent être stockées en dehors des clés de fuseau horaire du système dans le registre.)

Le stockage d’une chaîne de fuseau horaire sérialisée de cette manière sépare également la routine de création de fuseau horaire de l’application elle-même. Par exemple, une routine de création de fuseau horaire peut exécuter et créer un fichier de données qui contient les informations de fuseau horaire historiques qu’une application peut utiliser. Le fichier de données peut être ensuite installé avec l’application et peut être ouvert et un ou plusieurs de ses fuseaux horaires peuvent être désérialisés lorsque l’application en a besoin.

Pour obtenir un exemple qui utilise une ressource incorporée pour stocker des données de fuseau horaire sérialisées, consultez [Comment : enregistrer des fuseaux horaires dans une ressource incorporée](save-time-zones-to-an-embedded-resource.md) et [Comment : restaurer des fuseaux horaires à partir d’une ressource incorporée](restore-time-zones-from-an-embedded-resource.md).

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](index.md)
