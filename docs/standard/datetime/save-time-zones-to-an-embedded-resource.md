---
title: 'Procédure : enregistrer des fuseaux horaires dans une ressource incorporée'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], saving
- time zone objects [.NET Framework], serializing
- time zone objects [.NET Framework], saving
ms.assetid: 3c96d83a-a057-4496-abb0-8f4b12712558
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9ca39d989cc7bc16ec2678ba5fa53710899f3ac4
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70107159"
---
# <a name="how-to-save-time-zones-to-an-embedded-resource"></a>Procédure : enregistrer des fuseaux horaires dans une ressource incorporée

Une application prenant en charge les fuseaux horaires requiert souvent la présence d’un fuseau horaire particulier. Toutefois, étant donné que la disponibilité <xref:System.TimeZoneInfo> d’objets individuels dépend des informations stockées dans le Registre du système local, les fuseaux horaires habituellement disponibles peuvent être absents. En outre, les informations sur les fuseaux horaires personnalisés instanciées <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> à l’aide de la méthode ne sont pas stockées avec d’autres informations de fuseau horaire dans le registre. Pour vous assurer que ces fuseaux horaires sont disponibles lorsqu’ils sont nécessaires, vous pouvez les enregistrer en les sérialisant et les restaurer ultérieurement en les désérialisant.

En général, la sérialisation <xref:System.TimeZoneInfo> d’un objet se produit en dehors de l’application prenant en charge les fuseaux horaires. Selon le magasin de données utilisé pour stocker les <xref:System.TimeZoneInfo> objets sérialisés, les données de fuseau horaire peuvent être sérialisées dans le cadre d’une routine d’installation ou d’installation (par exemple, lorsque les données sont stockées dans une clé d’application du registre) ou dans le cadre d’une routine utilitaire qui s’exécute avant la compilation de l’application finale (par exemple, lorsque les données sérialisées sont stockées dans un fichier de ressources XML .NET (. resx)).

En plus d’un fichier de ressources compilé avec l’application, plusieurs autres magasins de données peuvent être utilisés pour les informations de fuseau horaire. Notamment :

- Registre. Notez qu’une application doit utiliser les sous-clés de sa propre clé d’application pour stocker des données de fuseau horaire personnalisées plutôt que d’utiliser les sous-clés de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time zones.

- Fichiers de configuration.

- Autres fichiers système.

### <a name="to-save-a-time-zone-by-serializing-it-to-a-resx-file"></a>Pour enregistrer un fuseau horaire en le sérialisant dans un fichier. resx

1. Récupérez un fuseau horaire existant ou créez un nouveau fuseau horaire.

   Pour récupérer un fuseau horaire existant, consultez [procédure: Accédez aux objets UTC et aux objets](../../../docs/standard/datetime/access-utc-and-local.md) de fuseau horaire local prédéfinis et [Comment: Instanciez un objet](../../../docs/standard/datetime/instantiate-time-zone-info.md)TimeZoneInfo.

   Pour créer un nouveau fuseau horaire, appelez l’une des surcharges de la <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> méthode. Pour plus d’informations, consultez [Guide pratique pour Créer des fuseaux horaires sans](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) règles [d’ajustement et procédure: Créer des fuseaux horaires avec](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md)des règles d’ajustement.

2. Appelez la <xref:System.TimeZoneInfo.ToSerializedString%2A> méthode pour créer une chaîne qui contient les données du fuseau horaire.

3. Instanciez <xref:System.IO.StreamWriter> un objet en fournissant le nom et éventuellement le chemin d’accès du fichier. resx <xref:System.IO.StreamWriter> au constructeur de classe.

4. Instanciez <xref:System.Resources.ResXResourceWriter> un objet en passant <xref:System.IO.StreamWriter> l’objet au <xref:System.Resources.ResXResourceWriter> constructeur de classe.

5. Transmettez la chaîne sérialisée du fuseau horaire à <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> la méthode.

6. Appelez la méthode <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType>.

7. Appelez la méthode <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType>.

8. Fermez l' <xref:System.IO.StreamWriter> objet en appelant sa <xref:System.IO.StreamWriter.Close%2A> méthode.

9. Ajoutez le fichier. resx généré au projet Visual Studio de l’application.

10. À l’aide de la fenêtre **Propriétés** dans Visual Studio, assurez-vous que la propriété **action de génération** du fichier. resx est définie sur **ressource incorporée**.

## <a name="example"></a>Exemple

L’exemple suivant sérialise un <xref:System.TimeZoneInfo> objet qui représente l’heure centrale et un <xref:System.TimeZoneInfo> objet qui représente la station de Palmer, en Antarctique, sur un fichier de ressources .net XML nommé SerializedTimeZones. resx. L’heure standard centrale est généralement définie dans le registre. Palmer station, Antarctique est un fuseau horaire personnalisé.

[!code-csharp[TimeZone2.Serialization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#1)]
[!code-vb[TimeZone2.Serialization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#1)]

Cet exemple sérialise <xref:System.TimeZoneInfo> les objets afin qu’ils soient disponibles dans un fichier de ressources au moment de la compilation.

Étant donné <xref:System.Resources.ResXResourceWriter.Generate%2A?displayProperty=nameWithType> que la méthode ajoute des informations d’en-tête complètes à un fichier de ressources XML .net, elle ne peut pas être utilisée pour ajouter des ressources à un fichier existant. L’exemple gère cela en recherchant le fichier SerializedTimeZones. resx et, le cas échéant, en stockant toutes ses ressources autres que les fuseaux horaires sérialisées dans un objet <xref:System.Collections.Generic.Dictionary%602> générique. Le fichier existant est ensuite supprimé et les ressources existantes sont ajoutées à un nouveau fichier SerializedTimeZones. resx. Les données de fuseau horaire sérialisées sont également ajoutées à ce fichier.

Les champs de clé (ou de **nom**) des ressources ne doivent pas contenir d’espaces incorporés. La <xref:System.String.Replace%28System.String%2CSystem.String%29> méthode est appelée pour supprimer tous les espaces incorporés dans les identificateurs de fuseau horaire avant de les assigner au fichier de ressources.

## <a name="compiling-the-code"></a>Compilation du code

Cet exemple nécessite :

- Qu’une référence à System. Windows. Forms. dll et System. Core. dll soit ajoutée au projet.

- Que les espaces de noms suivants soient importés:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
- [Vue d’ensemble des fuseaux horaires](../../../docs/standard/datetime/time-zone-overview.md)
- [Guide pratique pour Restaurer des fuseaux horaires à partir d’une ressource incorporée](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md)
