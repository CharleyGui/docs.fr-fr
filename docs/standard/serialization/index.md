---
title: Sérialisation dans .NET
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 13ba804e76a64c6a0b32ba5a203258e76c209ff4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644911"
---
# <a name="serialization-in-net"></a>Sérialisation dans .NET
La sérialisation correspond au processus de conversion de l'état d'un objet en un formulaire persistant ou transportable. Le complément de la sérialisation est la désérialisation, qui convertit un flux de données en un objet. Ces deux processus permettent de stocker et de transférer facilement des données.  
  
.NET comprend deux technologies de sérialisation :  
  
- La sérialisation binaire préserve le respect des types, qui permet de conserver l'état d'un objet entre plusieurs appels d'une application. Par exemple, vous pouvez partager un objet entre plusieurs applications en le sérialisant dans le Presse-papiers. Vous pouvez sérialiser un objet vers un flux, un disque, la mémoire, le réseau, et ainsi de suite. La communication à distance utilise la sérialisation pour passer des objets « par valeur » d'un ordinateur ou d'un domaine d'application à un autre.  
  
- La sérialisation XML sérialise uniquement des propriétés et des champs publics mais ne conserve pas le respect des types. Ceci est utile lorsque vous souhaitez fournir ou consommer des données sans restreindre l'application qui les utilise. XML étant une norme ouverte, elle constitue une option intéressante pour partager des données via le Web. Le protocole SOAP est également une norme ouverte et représente par conséquent une option avantageuse.  
  
## <a name="in-this-section"></a>Dans cette section  
[Rubriques de guides pratiques pour la sérialisation](../../../docs/standard/serialization/serialization-how-to-topics.md)  
Répertorie les liens vers les rubriques Comment contenues dans cette section.
  
[Sérialisation binaire](../../../docs/standard/serialization/binary-serialization.md)  
Décrit le mécanisme de sérialisation binaire inclus avec le Common Language Runtime.

[Sérialisation XML et SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
Décrit le mécanisme de sérialisation XML et SOAP inclus avec le Common Language Runtime.

[Outils de sérialisation](../../../docs/standard/serialization/serialization-tools.md)  
Ces outils vous aident à développer le code de sérialisation.

[Exemples de sérialisation](../../../docs/standard/serialization/serialization-samples.md)  
Les exemples montrent comment procéder à la sérialisation.

## <a name="reference"></a>Référence
<xref:System.Runtime.Serialization> contient des classes qui peuvent être utilisées pour sérialiser et désérialiser des objets.
  
<xref:System.Xml.Serialization>  
Contient des classes qui peuvent être utilisées pour sérialiser des objets en documents ou en flux de données au format XML.