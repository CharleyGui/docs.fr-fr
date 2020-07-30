---
title: Sérialisation (C#)
description: La sérialisation convertit un objet en un flux d’octets pour stocker l’objet ou le transmettre à la mémoire, à une base de données ou à un fichier.
ms.date: 01/02/2020
ms.openlocfilehash: b2b3105887ad6f000fcba895452a483881ae5a09
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302774"
---
# <a name="serialization-c"></a>Sérialisation (C#)

La sérialisation est le processus de conversion d’un objet en flux d’octets pour stocker l’objet ou le transmettre à la mémoire, une base de données ou un fichier. Son principal objectif est d’enregistrer l’état d’un objet afin de pouvoir le recréer si nécessaire. Le processus inverse est appelé désérialisation.

## <a name="how-serialization-works"></a>Fonctionnement de la sérialisation

Cette illustration montre le processus global de sérialisation :

![Graphique sérialisation](./media/index/serialization-process.gif)

L’objet est sérialisé en un flux qui contient les données. Le flux peut également contenir des informations sur le type de l’objet, telles que sa version, sa culture et son nom d’assembly. À partir de ce flux, l’objet peut être stocké dans une base de données, un fichier ou une mémoire.

### <a name="uses-for-serialization"></a>Usages de la sérialisation

La sérialisation permet au développeur d’enregistrer l’état d’un objet et de le recréer en fonction des besoins, en fournissant le stockage des objets ainsi que l’échange de données. Par le biais de la sérialisation, un développeur peut effectuer des actions telles que :

* Envoi de l’objet à une application distante à l’aide d’un service Web
* Passage d’un objet d’un domaine à un autre
* Passage d’un objet via un pare-feu sous forme de chaîne JSON ou XML
* Gestion des informations relatives à la sécurité ou aux utilisateurs entre les applications

## <a name="json-serialization"></a>Sérialisation JSON

L' <xref:System.Text.Json> espace de noms contient des classes pour la sérialisation et la désérialisation JavaScript Object Notation (JSON). JSON est une norme ouverte qui est couramment utilisée pour partager des données sur le Web.

La sérialisation JSON sérialise les propriétés publiques d’un objet dans une chaîne, un tableau d’octets ou un flux conforme à [la spécification JSON RFC 8259](https://tools.ietf.org/html/rfc8259). Pour contrôler la manière dont <xref:System.Text.Json.JsonSerializer> sérialise ou désérialise une instance de la classe :

* Utiliser un <xref:System.Text.Json.JsonSerializerOptions> objet
* Appliquer des attributs de l' <xref:System.Text.Json.Serialization> espace de noms à des classes ou des propriétés
* [Implémenter des convertisseurs personnalisés](../../../../standard/serialization/system-text-json-converters-how-to.md)

## <a name="binary-and-xml-serialization"></a>Sérialisation binaire et XML

L' <xref:System.Runtime.Serialization> espace de noms contient des classes pour la sérialisation et la désérialisation binaires et XML.

La sérialisation binaire utilise l’encodage binaire pour produire une sérialisation compacte qui peut servir notamment aux flux réseau par socket ou stockage. Dans la sérialisation binaire, tous les membres, y compris en lecture seule, sont sérialisés et les performances sont améliorées.

La sérialisation XML sérialise les champs et les propriétés publics d’un objet ou les paramètres et valeurs renvoyés de méthodes, en un flux XML conforme à un document XSD (langage de définition de schéma XML) spécifique. La sérialisation XML permet d’obtenir des classes fortement typées avec des propriétés et des champs publics convertis au format XML. <xref:System.Xml.Serialization>contient des classes pour sérialiser et désérialiser du code XML. Vous pouvez appliquer des attributs à des classes et des membres de classes pour contrôler la manière dont <xref:System.Xml.Serialization.XmlSerializer> sérialise ou désérialise une instance de la classe.

### <a name="making-an-object-serializable"></a>Rendre un objet sérialisable

Pour la sérialisation binaire ou XML, vous avez besoin des éléments suivants :

* Objet à sérialiser.
* Flux destiné à contenir l’objet sérialisé
* Une <xref:System.Runtime.Serialization.Formatter?displayProperty=fullName> instance

Appliquez l' <xref:System.SerializableAttribute> attribut à un type pour indiquer que les instances du type peuvent être sérialisées. Une exception est levée si vous tentez une sérialisation alors que le type n’a pas l’attribut <xref:System.SerializableAttribute>.

Pour empêcher la sérialisation d’un champ, appliquez l' <xref:System.NonSerializedAttribute> attribut. Si un champ d’un type sérialisable contient un pointeur, un handle ou une autre structure de données propre à un environnement particulier et qu’il n’est pas possible de le reconstituer de manière significative dans un autre environnement, vous pouvez le rendre non sérialisable.

Si une classe sérialisée contient des références à des objets d’autres classes marqués par <xref:System.SerializableAttribute>, ces objets seront également sérialisés.

### <a name="basic-and-custom-serialization"></a>Sérialisation de base et sérialisation personnalisée

La sérialisation binaire et XML peut être effectuée de deux manières, de base et personnalisée.

La sérialisation de base utilise .NET pour sérialiser automatiquement l’objet. La seule exigence est que l’attribut est appliqué à la classe <xref:System.SerializableAttribute> . <xref:System.NonSerializedAttribute> peut être utilisé pour empêcher que certains champs ne soient sérialisés.

Quand vous utilisez la sérialisation de base, le contrôle de version des objets peut créer des problèmes. Vous pouvez utiliser la sérialisation personnalisée quand les problèmes de contrôle de version sont importants. La sérialisation de base est le moyen le plus simple d’effectuer la sérialisation, mais elle ne fournit pas beaucoup de contrôle sur le processus.

Dans la sérialisation personnalisée, vous pouvez spécifier exactement quels objets sont sérialisés et de quelle façon. La classe doit être marquée <xref:System.SerializableAttribute> et implémenter l’interface <xref:System.Runtime.Serialization.ISerializable>. Si vous souhaitez également que votre objet soit désérialisé de manière personnalisée, utilisez un constructeur personnalisé.

## <a name="designer-serialization"></a>Sérialisation du concepteur

La sérialisation du concepteur est une forme particulière de sérialisation qui implique le type de persistance d’objets associé aux outils de développement. La sérialisation du concepteur est le processus qui consiste à convertir un graphique d’objet en un fichier source utilisable ultérieurement pour récupérer le graphique d’objet. Un fichier source peut contenir du code, des balises ou même des tables SQL.

## <a name="related-topics-and-examples"></a><a name="BKMK_RelatedTopics"></a> Rubriques connexes et exemples  

[Présentation deSystem.Text.Js](../../../../standard/serialization/system-text-json-overview.md) Montre comment récupérer la `System.Text.Json` bibliothèque.

[Comment sérialiser et désérialiser JSON dans .net](../../../../standard/serialization/system-text-json-how-to.md).
Montre comment lire et écrire des données d’objet dans et à partir de JSON à l’aide de la <xref:System.Text.Json.JsonSerializer> classe.

[Procédure pas à pas : persistance d’un objet dans Visual Studio (C#)](walkthrough-persisting-an-object-in-visual-studio.md)  
Montre comment utiliser la sérialisation pour rendre les données d’un objet persistantes entre les instances, afin de stocker des valeurs et de les récupérer lors de la prochaine instanciation de l’objet.

[Comment lire des données d’objet à partir d’un fichier XML (C#)](how-to-read-object-data-from-an-xml-file.md)  
Montre comment lire les données d’objet écrites précédemment dans un fichier XML en utilisant la classe <xref:System.Xml.Serialization.XmlSerializer>.

[Comment écrire des données d’objet dans un fichier XML (C#)](how-to-write-object-data-to-an-xml-file.md)  
Montre comment écrire l’objet depuis une classe vers un fichier XML en utilisant la classe <xref:System.Xml.Serialization.XmlSerializer>.
