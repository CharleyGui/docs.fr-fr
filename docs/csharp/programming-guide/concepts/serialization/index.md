---
title: Sérialisation (C#)
ms.date: 01/02/2020
ms.openlocfilehash: d914298a370b09307e84c88959542b4823cf37ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167593"
---
# <a name="serialization-c"></a>Sérialisation (C#)

La sérialisation est le processus de conversion d’un objet en flux d’octets pour stocker l’objet ou le transmettre à la mémoire, une base de données ou un fichier. Son principal objectif est d’enregistrer l’état d’un objet afin de pouvoir le recréer si nécessaire. Le processus inverse est appelé désérialisation.

## <a name="how-serialization-works"></a>Fonctionnement de la sérialisation

Cette illustration montre le processus global de sérialisation :

![Graphique sérialisation](./media/index/serialization-process.gif)

L’objet est sérialisé sur un flux qui transporte les données. Le flux peut également avoir des informations sur le type de l’objet, tels que sa version, sa culture et son nom d’assemblage. À partir de ce flux, l’objet peut être stocké dans une base de données, un fichier ou une mémoire.

### <a name="uses-for-serialization"></a>Usages de la sérialisation

La sérialisation permet au développeur de sauver l’état d’un objet et de le recréer au besoin, en fournissant le stockage d’objets ainsi que l’échange de données. Grâce à la sérialisation, un développeur peut effectuer des actions telles que :

* Envoi de l’objet à une application distante à l’aide d’un service web
* Passer un objet d’un domaine à un autre
* Passer un objet à travers un pare-feu comme une chaîne JSON ou XML
* Maintenir la sécurité ou les informations spécifiques à l’utilisateur sur toutes les applications

## <a name="json-serialization"></a>Sérialisation JSON

L’espace <xref:System.Text.Json> de nom contient des classes pour la sérialisation et la désétérialisation JavaScript Object Notation (JSON). JSON est une norme ouverte qui est couramment utilisée pour le partage de données sur le Web.

La sérialisation JSON sérialisse les propriétés publiques d’un objet en une chaîne, un tableau d’orte ou un flux conforme aux [spécifications de RFC 8259 JSON](https://tools.ietf.org/html/rfc8259). Pour contrôler <xref:System.Text.Json.JsonSerializer> la façon dont la sérialisation ou désélise un exemple de la classe :

* Utiliser <xref:System.Text.Json.JsonSerializerOptions> un objet
* Appliquer les attributs de l’espace <xref:System.Text.Json.Serialization> nom aux classes ou aux propriétés
* [Implémenter les convertisseurs personnalisés](../../../../standard/serialization/system-text-json-converters-how-to.md)

## <a name="binary-and-xml-serialization"></a>Sérialisation binaire et XML

L’espace <xref:System.Runtime.Serialization> de nom contient des classes pour la sérialisation binaire et XML et la désétérialisation.

La sérialisation binaire utilise l’encodage binaire pour produire une sérialisation compacte qui peut servir notamment aux flux réseau par socket ou stockage. Dans la sérialisation binaire, tous les membres, y compris en lecture seule, sont sérialisés et les performances sont améliorées.

La sérialisation XML sérialise les champs et les propriétés publics d’un objet ou les paramètres et valeurs renvoyés de méthodes, en un flux XML conforme à un document XSD (langage de définition de schéma XML) spécifique. La sérialisation XML permet d’obtenir des classes fortement typées avec des propriétés et des champs publics convertis au format XML. <xref:System.Xml.Serialization>contient des cours de sérialisation et de désétérialisation de XML. Vous pouvez appliquer des attributs à des classes et des membres de classes pour contrôler la manière dont <xref:System.Xml.Serialization.XmlSerializer> sérialise ou désérialise une instance de la classe.

### <a name="making-an-object-serializable"></a>Rendre un objet sérialisable

Pour la sérialisation binaire ou XML, vous avez besoin :

* L’objet à sérialiser
* Un flux pour contenir l’objet sérialisé
* Un <xref:System.Runtime.Serialization.Formatter?displayProperty=fullName> exemple

Appliquer <xref:System.SerializableAttribute> l’attribut à un type pour indiquer que les instances du type peuvent être sérialisées. Une exception est levée si vous tentez une sérialisation alors que le type n’a pas l’attribut <xref:System.SerializableAttribute>.

Pour éviter qu’un champ ne <xref:System.NonSerializedAttribute> soit sérialisé, appliquez l’attribut. Si un champ d’un type sérialisable contient un pointeur, un handle ou une autre structure de données propre à un environnement particulier et qu’il n’est pas possible de le reconstituer de manière significative dans un autre environnement, vous pouvez le rendre non sérialisable.

Si une classe sérialisée contient des références à des objets d’autres classes marqués par <xref:System.SerializableAttribute>, ces objets seront également sérialisés.

### <a name="basic-and-custom-serialization"></a>Sérialisation de base et sérialisation personnalisée

La sérialisation binaire et XML peut être effectuée de deux façons, de base et de coutume.

La sérialisation de base utilise .NET Framework pour sérialiser automatiquement l’objet. La seule exigence est que <xref:System.SerializableAttribute> la classe a l’attribut appliqué. <xref:System.NonSerializedAttribute> peut être utilisé pour empêcher que certains champs ne soient sérialisés.

Quand vous utilisez la sérialisation de base, le contrôle de version des objets peut créer des problèmes. Vous pouvez utiliser la sérialisation personnalisée quand les problèmes de contrôle de version sont importants. La sérialisation de base est le moyen le plus simple d’effectuer la sérialisation, mais elle ne fournit pas beaucoup de contrôle sur le processus.

Dans la sérialisation personnalisée, vous pouvez spécifier exactement quels objets sont sérialisés et de quelle façon. La classe doit être marquée <xref:System.SerializableAttribute> et implémenter l’interface <xref:System.Runtime.Serialization.ISerializable>. Si vous voulez que votre objet soit déséialisé d’une manière personnalisée ainsi, utilisez un constructeur personnalisé.

## <a name="designer-serialization"></a>Sérialisation du concepteur

La sérialisation du concepteur est une forme particulière de sérialisation qui implique le type de persistance d’objets associé aux outils de développement. La sérialisation du concepteur est le processus qui consiste à convertir un graphique d’objet en un fichier source utilisable ultérieurement pour récupérer le graphique d’objet. Un fichier source peut contenir du code, des balises ou même des tables SQL.

## <a name="BKMK_RelatedTopics"></a> Rubriques connexes et exemples  

[Aperçu de System.Text.Json](../../../../standard/serialization/system-text-json-overview.md) Montre comment obtenir `System.Text.Json` la bibliothèque.

[Comment sérialiser et déséialiser JSON en .NET](../../../../standard/serialization/system-text-json-how-to.md).
Montre comment lire et écrire des données d’objet à et de JSON en utilisant la <xref:System.Text.Json.JsonSerializer> classe.

[Procédure pas à pas : persistance d’un objet dans Visual Studio (C#)](walkthrough-persisting-an-object-in-visual-studio.md)  
Montre comment utiliser la sérialisation pour rendre les données d’un objet persistantes entre les instances, afin de stocker des valeurs et de les récupérer lors de la prochaine instanciation de l’objet.

[Comment lire les données d’objets à partir d’un fichier XML (C)](how-to-read-object-data-from-an-xml-file.md)  
Montre comment lire les données d’objet écrites précédemment dans un fichier XML en utilisant la classe <xref:System.Xml.Serialization.XmlSerializer>.

[Comment écrire des données d’objet à un fichier XML (C)](how-to-write-object-data-to-an-xml-file.md)  
Montre comment écrire l’objet depuis une classe vers un fichier XML en utilisant la classe <xref:System.Xml.Serialization.XmlSerializer>.
