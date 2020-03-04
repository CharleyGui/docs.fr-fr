---
title: Concepts de la sérialisation
ms.date: 08/07/2017
ms.assetid: e1ff4740-20a1-4c76-a8ad-d857db307054
ms.openlocfilehash: 1a7fa7c3e5561fc9e48cf627a703abc747a72ba0
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159830"
---
# <a name="serialization-concepts"></a>Concepts de la sérialisation
Pourquoi utiliser la sérialisation ? L'une des deux raisons majeures est que vous pouvez, d'une part, rendre persistant l'état d'un objet sur un support de stockage afin qu'une copie exacte puisse être recréée ultérieurement. D'autre part, vous pouvez envoyer cet objet par valeur d'un domaine d'application à l'autre. Par exemple, la sérialisation est utilisée pour enregistrer l'état de session dans ASP.NET et copier des objets vers le Presse-papiers dans les Windows Forms. Elle est également utilisée par la communication à distance pour passer des objets par valeur d'un domaine d'application à un autre.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="persistent-storage"></a>Stockage persistant
Il est souvent nécessaire de stocker la valeur des champs d'un objet sur un disque pour pouvoir récupérer ces données ultérieurement. Bien que cela soit facile à accomplir sans utiliser la sérialisation, cette méthode est souvent fastidieuse et susceptible d'entraîner des erreurs. Elle devient en outre de plus en plus complexe lorsque vous devez suivre une hiérarchie d'objets. Imaginez que vous deviez enregistrer des données au sein d'une grande application d'entreprise qui contient des milliers d'objets et que vous deviez écrire du code pour enregistrer et restaurer des champs et propriétés sur et à partir d'un disque pour chaque objet. La sérialisation offre un mécanisme pratique permettant d'atteindre cet objectif.

Le Common Language Runtime gère la manière dont les objets sont stockés en mémoire et fournit un mécanisme de sérialisation automatisé par le biais de la [réflexion](../../../docs/framework/reflection-and-codedom/reflection.md). Lorsqu'un objet est sérialisé, le nom de la classe, l'assembly et tous les membres de données de l'instance de classe sont écrits sur le support de stockage. Les objets stockent souvent des références à d'autres instances dans les variables membres. Lorsque la classe est sérialisée, le moteur de sérialisation effectue un suivi des objets référencés et déjà sérialisés, pour garantir qu'un même objet n'est pas sérialisé plusieurs fois. L’architecture de sérialisation fournie avec le .NET Framework gère correctement les graphiques d’objets et les références circulaires. La seule spécification définie pour les graphiques d’objets est que tous les objets référencés par l’objet sérialisé doivent également être marqués comme `Serializable` (pour plus d’informations, consultez [Sérialisation de base](basic-serialization.md)). Si tel n'est pas le cas, une exception est levée lorsque le sérialiseur tente de sérialiser l'objet non marqué.

Quand la classe sérialisée est désérialisée, elle est recréée et les valeurs de toutes les données membres sont restaurées automatiquement.

## <a name="marshal-by-value"></a>Marshaler par valeur
Les objets sont uniquement valides dans le domaine d'application au sein duquel ils ont été créés. Toute tentative de passer l’objet comme paramètre ou de le retourner comme résultat échoue si l’objet dérive de `MarshalByRefObject` ou est marqué comme `Serializable`. Si l’objet est marqué comme `Serializable`, il est automatiquement sérialisé, passé du domaine d’application à l’autre, puis désérialisé pour en générer une copie exacte dans le deuxième domaine d’application. Ce processus est en général connu sous le nom de marshaling par valeur.

Quand un objet dérive de `MarshalByRefObject`, une référence de l’objet (et non l’objet lui-même) est passée d’un domaine d’application à un autre. Vous pouvez également marquer un objet qui dérive de `MarshalByRefObject` comme `Serializable`. Quand cet objet est utilisé avec la communication à distance, le formateur responsable de la sérialisation, préconfiguré avec un sélecteur de substitut (`SurrogateSelector`), prend le contrôle du processus de sérialisation et remplace tous les objets dérivés de `MarshalByRefObject` par un proxy. Si `SurrogateSelector` n’est pas défini, l’architecture de sérialisation suit les règles de sérialisation standard décrites dans [Étapes du processus de sérialisation](steps-in-the-serialization-process.md).  

## <a name="related-sections"></a>Sections connexes  
 [Sérialisation binaire](../../../docs/standard/serialization/binary-serialization.md)  
 Décrit le mécanisme de sérialisation binaire inclus avec le Common Language Runtime.  
  
 \ [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))
 Décrit les différentes méthodes de communication disponibles dans le .NET Framework pour les communications distantes.  
  
 [Sérialisation XML et SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 Décrit le mécanisme de sérialisation XML et SOAP inclus avec le Common Language Runtime.
