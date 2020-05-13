---
title: Étapes du processus de sérialisation
description: Le processus de sérialisation commence lorsque la méthode Serialize est appelée sur un formateur. Cet article décrit la séquence d’événements.
ms.date: 08/07/2017
helpviewer_keywords:
- binary serialization, steps
- serialization, steps
ms.assetid: 4bcbc883-2a91-418f-b968-6c86a25e9737
ms.openlocfilehash: 1f749b9102182e78bc3fda436cf386a9f5759d5a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379102"
---
# <a name="steps-in-the-serialization-process"></a>Étapes du processus de sérialisation
Quand la méthode <xref:System.Runtime.Serialization.Formatter.Serialize%2A> est appelée sur un [formateur](xref:System.Runtime.Serialization.Formatter), la sérialisation de l’objet s’effectue d’après la séquence de règles suivante :

- Un contrôle est effectué pour déterminer si le formateur possède un sélecteur de substitut. Si tel est le cas, vérifiez si le sélecteur de substitut gère des objets du type donné. Si le sélecteur gère le type d’objet, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> est appelée sur le sélecteur de substitution.

- S’il n’existe aucun sélecteur de substitution ou s’il ne gère pas ce type d’objet, un contrôle est effectué pour déterminer si l’objet est marqué avec l’attribut [Serializable](xref:System.SerializableAttribute). S’il ne l’est pas, une exception <xref:System.Runtime.Serialization.SerializationException> est levée.

- Si l’objet est marqué convenablement, vérifiez s’il implémente l’interface <xref:System.Runtime.Serialization.ISerializable>. Si tel est le cas, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> est appelée sur l’objet.
  
- Si l’objet n’implémente pas <xref:System.Runtime.Serialization.ISerializable>, la stratégie de sérialisation par défaut est utilisée. Elle permet de sérialiser tous les champs non marqués comme [NonSerialized](xref:System.NonSerializedAttribute).

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
## <a name="see-also"></a>Voir aussi

- [Sérialisation binaire](binary-serialization.md)
- [Sérialisation XML et SOAP](xml-and-soap-serialization.md)
