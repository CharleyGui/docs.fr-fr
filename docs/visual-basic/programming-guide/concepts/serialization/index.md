---
title: Sérialisation
ms.date: 07/20/2015
ms.assetid: 67379a76-5465-4af8-a781-0b0b25a62d9a
ms.openlocfilehash: 98400c9e7ed9e26a9dc6ca548988c3691bfecdc2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086502"
---
# <a name="serialization-visual-basic"></a>Sérialisation (Visual Basic)

La sérialisation est le processus de conversion d'un objet en un flux d'octets pour stocker l'objet ou le transmettre à la mémoire, à une base de données, ou dans un fichier. Son principal objectif est d’enregistrer l’état d’un objet afin de pouvoir le recréer si nécessaire. Le processus inverse est appelé désérialisation.  
  
## <a name="how-serialization-works"></a>Fonctionnement de la sérialisation  

 Cette illustration montre le processus global de sérialisation.  
  
![Graphique sérialisation](./media/index/serialization-process.gif)
  
 L’objet est sérialisé en un flux, qui contient non seulement les données, mais aussi des informations sur le type de l’objet, telles que sa version, sa culture et son nom d’assembly. À partir de ce flux, il peut être stocké dans une base de données, dans un fichier ou en mémoire.  
  
### <a name="uses-for-serialization"></a>Usages de la sérialisation  

 La sérialisation permet au développeur d’enregistrer l’état d’un objet et de le recréer si nécessaire, en fournissant le stockage d’objets, ainsi que l’échange de données. Avec la sérialisation, un développeur peut effectuer des actions comme envoyer l’objet à une application distante au moyen d’un service web, le transmettre d’un domaine à un autre, le transmettre à travers un pare-feu sous forme de chaîne XML ou maintenir la sécurité ou des informations propres à l’utilisateur entre les applications.  
  
### <a name="making-an-object-serializable"></a>Rendre un objet sérialisable  

 Pour sérialiser un objet, il vous faut l’objet à sérialiser, un flux qui contiendra l’objet sérialisé et <xref:System.Runtime.Serialization.Formatter>. <xref:System.Runtime.Serialization> contient les classes nécessaires pour sérialiser et désérialiser des objets.  
  
 Appliquez l’attribut <xref:System.SerializableAttribute> à un type pour indiquer que les instances de ce type peuvent être sérialisées. Une exception <xref:System.Runtime.Serialization.SerializationException> est levée si vous tentez de sérialiser alors que le type n’a pas l’attribut <xref:System.SerializableAttribute>.  
  
 Si vous ne voulez pas qu’un champ de votre classe soit sérialisable, appliquez l’attribut <xref:System.NonSerializedAttribute>. Si un champ d’un type sérialisable contient un pointeur, un handle ou une autre structure de données propre à un environnement particulier et qu’il n’est pas possible de le reconstituer de manière significative dans un autre environnement, vous pouvez le rendre non sérialisable.  
  
 Si une classe sérialisée contient des références à des objets d’autres classes marqués par <xref:System.SerializableAttribute>, ces objets seront également sérialisés.  
  
## <a name="binary-and-xml-serialization"></a>Sérialisation binaire et XML  

 Il est possible d’utiliser soit la sérialisation binaire soit la sérialisation XML. Dans la sérialisation binaire, tous les membres, y compris en lecture seule, sont sérialisés et les performances sont améliorées. La sérialisation XML fournit un code plus lisible, ainsi qu’une plus grande souplesse de partage et d’utilisation de l’objet à des fins d’interopérabilité.  
  
### <a name="binary-serialization"></a>Sérialisation binaire  

 La sérialisation binaire utilise l’encodage binaire pour produire une sérialisation compacte qui peut servir notamment aux flux réseau par socket ou stockage.  
  
### <a name="xml-serialization"></a>Sérialisation XML  

 La sérialisation XML sérialise les champs et les propriétés publics d’un objet ou les paramètres et valeurs renvoyés de méthodes, en un flux XML conforme à un document XSD (langage de définition de schéma XML) spécifique. La sérialisation XML permet d’obtenir des classes fortement typées avec des propriétés et des champs publics convertis au format XML. <xref:System.Xml.Serialization> contient les classes nécessaires pour sérialiser et désérialiser du code XML.  
  
 Vous pouvez appliquer des attributs à des classes et des membres de classes afin de contrôler la manière dont <xref:System.Xml.Serialization.XmlSerializer> sérialise ou désérialise une instance de la classe.  
  
## <a name="basic-and-custom-serialization"></a>Sérialisation de base et sérialisation personnalisée  

 La sérialisation peut s’effectuer de deux manières : de base et personnalisée. La sérialisation de base utilise .NET Framework pour sérialiser automatiquement l’objet.  
  
### <a name="basic-serialization"></a>Sérialisation de base  

 La seule condition pour la sérialisation de base est que l’attribut <xref:System.SerializableAttribute> soit appliqué à l’objet. <xref:System.NonSerializedAttribute> peut être utilisé pour empêcher que certains champs ne soient sérialisés.  
  
 Lorsque vous utilisez la sérialisation de base, la gestion des versions des objets peut poser problème, auquel cas la sérialisation personnalisée peut être préférable. La sérialisation de base est le moyen le plus simple d’effectuer la sérialisation, mais elle ne fournit pas beaucoup de contrôle sur le processus.  
  
### <a name="custom-serialization"></a>Sérialisation personnalisée  

 Dans la sérialisation personnalisée, vous pouvez spécifier exactement quels objets sont sérialisés et de quelle façon. La classe doit être marquée <xref:System.SerializableAttribute> et implémenter l’interface <xref:System.Runtime.Serialization.ISerializable>.  
  
 Si vous souhaitez que votre objet soit également désérialisé de manière personnalisée, vous devez utiliser un constructeur personnalisé.  
  
## <a name="designer-serialization"></a>Sérialisation du concepteur  

 La sérialisation du concepteur est une forme particulière de sérialisation qui implique le type de persistance d’objets généralement associé aux outils de développement. La sérialisation du concepteur est le processus qui consiste à convertir un graphique d’objet en un fichier source utilisable ultérieurement pour récupérer le graphique d’objet. Un fichier source peut contenir du code, des balises ou même des tables SQL.  
  
## <a name="related-topics-and-examples"></a><a name="BKMK_RelatedTopics"></a> Rubriques connexes et exemples  

 [Procédure pas à pas : persistance d’un objet dans Visual Studio (Visual Basic)](walkthrough-persisting-an-object-in-visual-studio.md)  
 Montre comment utiliser la sérialisation pour rendre les données d’un objet persistantes entre les instances, afin de stocker des valeurs et de les récupérer lors de la prochaine instanciation de l’objet.  
  
 [Guide pratique : lire des données d’objet à partir d’un fichier XML (Visual Basic)](how-to-read-object-data-from-an-xml-file.md)  
 Montre comment lire les données d’objet écrites précédemment dans un fichier XML en utilisant la classe <xref:System.Xml.Serialization.XmlSerializer>.  
  
 [Guide pratique : écrire des données d’objet dans un fichier XML (Visual Basic)](how-to-write-object-data-to-an-xml-file.md)  
 Montre comment écrire l’objet depuis une classe vers un fichier XML en utilisant la classe <xref:System.Xml.Serialization.XmlSerializer>.
