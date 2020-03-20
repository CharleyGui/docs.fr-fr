---
title: 'Atténuation : désérialisation des objets à travers les domaines d’application'
ms.date: 03/30/2017
ms.assetid: 30c2d66c-04a8-41a5-ad31-646b937f61b5
ms.openlocfilehash: e2d90a77cab699646bd31eaa162d1bd1744fd51b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457925"
---
# <a name="mitigation-deserialization-of-objects-across-app-domains"></a>Atténuation : désérialisation des objets à travers les domaines d’application
Dans certains cas, lorsqu'une application utilise plusieurs domaines d'application avec différentes bases d'application, la tentative de désérialiser des objets dans le contexte d'appel logique à travers des domaines d'application lève une exception.  
  
## <a name="diagnosing-the-issue"></a>Diagnostic du problème  
 Le problème survient dans la séquence suivante de conditions :  
  
1. Une application utilise deux voire plusieurs domaines d'application avec différentes bases d'application.  
  
2. Certains types sont ajoutés explicitement au <xref:System.Runtime.Remoting.Messaging.LogicalCallContext> en appelant une méthode comme <xref:System.Runtime.Remoting.Messaging.LogicalCallContext.SetData%2A?displayProperty=nameWithType> ou <xref:System.Runtime.Remoting.Messaging.CallContext.LogicalSetData%2A?displayProperty=nameWithType>. Ces types ne sont pas marqués comme étant sérialisables et ne sont pas inscrits dans le Global Assembly Cache.  
  
3. Ultérieurement, le code, qui s'exécute dans le domaine d'application qui n'est pas le domaine par défaut, essaie de lire une valeur d'un fichier de configuration ou d'utiliser XML pour désérialiser un objet.  
  
4. Afin de lire un fichier de configuration ou de désérialiser l'objet, un objet <xref:System.Xml.XmlReader> essaie d'accéder au système de configuration.  
  
5. Si le système de configuration n'a pas déjà été initialisé, il doit terminer son initialisation. Cela signifie, entre autres, que le runtime doit créer un tracé stable pour le système de configuration, ce qu'il fait comme suit :  
  
    1. Il recherche une preuve pour le domaine d'application qui n'est pas le domaine par défaut.  
  
    2. Il essaie de calculer la preuve pour le domaine d'application non défini par défaut, à partir du domaine d'application par défaut.  
  
    3. L'appel pour obtenir une preuve pour le domaine d'application par défaut déclenche un appel de domaines inter-applications à partir du domaine d'application non défini par défaut vers le domaine d'application par défaut.  
  
    4. Dans le cadre du contrat de domaines inter-applications du .NET Framework, le contenu du contexte d'appel logique doit être également marshalé à travers les frontières du domaine d'application.  
  
6. Parce que les types qui sont dans le contexte d'appel logique ne peuvent pas être résolus dans le domaine d'application par défaut, une exception est levée.  
  
## <a name="mitigation"></a>Limitation des risques  
 Pour contourner ce problème, procédez comme suit  
  
1. Recherchez l'appel à `get_Evidence` dans la pile des appels lorsque l'exception est levée. L'exception peut faire partie d'un grand sous-ensemble d'exceptions, notamment <xref:System.IO.FileNotFoundException> et <xref:System.Runtime.Serialization.SerializationException>.  
  
2. Identifiez l'emplacement de l'application dans lequel aucun objet n'est ajouté au contexte d'appel logique et ajoutez le code suivant :  
  
    ```csharp
    System.Configuration.ConfigurationManager.GetSection("system.xml/xmlReader");  
    ```
  
## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
