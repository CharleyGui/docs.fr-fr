---
title: Sérialisation-.NET
description: Cet article fournit des informations sur les technologies de sérialisation .NET, y compris la sérialisation binaire, la sérialisation XML et SOAP et la sérialisation JSON.
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: b3d76c14dc9180a5f19781122d1a42bcae603e76
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377244"
---
# <a name="serialization-in-net"></a>Sérialisation dans .NET

La sérialisation correspond au processus de conversion de l'état d'un objet en un formulaire persistant ou transportable. Le complément de la sérialisation est la désérialisation, qui convertit un flux de données en un objet. Ensemble, ces processus autorisent le stockage et le transfert des données.  
  
.NET propose les technologies de sérialisation suivantes :  
  
- [La sérialisation binaire](binary-serialization.md) préserve la fidélité du type, ce qui est utile pour conserver l’état d’un objet entre différents appels d’une application. Par exemple, vous pouvez partager un objet entre plusieurs applications en le sérialisant dans le Presse-papiers. Vous pouvez sérialiser un objet vers un flux, un disque, la mémoire, le réseau, et ainsi de suite. La communication à distance utilise la sérialisation pour passer des objets « par valeur » d'un ordinateur ou d'un domaine d'application à un autre.  
  
- [La sérialisation XML et SOAP](xml-and-soap-serialization.md) sérialise uniquement les propriétés et les champs publics et ne conserve pas la fidélité du type. Ceci est utile lorsque vous souhaitez fournir ou consommer des données sans restreindre l'application qui les utilise. XML étant une norme ouverte, elle constitue une option intéressante pour partager des données via le Web. Le protocole SOAP est également une norme ouverte et représente par conséquent une option avantageuse.  
  
- [La sérialisation JSON](system-text-json-overview.md) sérialise uniquement les propriétés publiques et ne conserve pas la fidélité du type. JSON est une norme ouverte qui est un choix attrayant pour le partage de données sur le Web.

## <a name="reference"></a>Informations de référence

<xref:System.Runtime.Serialization>  
Contient des classes qui peuvent être utilisées pour sérialiser et désérialiser des objets.
  
<xref:System.Xml.Serialization>  
Contient des classes qui peuvent être utilisées pour sérialiser des objets en documents ou en flux de données au format XML.

<xref:System.Text.Json>  
Contient des classes qui peuvent être utilisées pour sérialiser des objets dans des documents ou des flux au format JSON.
