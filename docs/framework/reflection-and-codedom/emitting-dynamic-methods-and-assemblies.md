---
title: Émission d'assemblys et de méthodes dynamiques
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: fda5a20eb7798086ec10415889454b4a8beba5f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180524"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>Émission d'assemblys et de méthodes dynamiques

Cette section décrit un ensemble de types managés dans l'espace de noms <xref:System.Reflection.Emit>, qui permettent à un compilateur ou à un outil d'émettre des métadonnées et du langage MSIL (Microsoft Intermediate Language) au moment de l'exécution et de générer éventuellement un fichier exécutable portable sur le disque. Les moteurs de script et les compilateurs sont les principaux utilisateurs de cet espace de noms. Dans cette section, la fonctionnalité fournies par l'espace de noms <xref:System.Reflection.Emit> est appelée émission de réflexion.  
  
L'émission de réflexion offre les possibilités suivantes :  
  
- Définir des méthodes globales légères au moment de l'exécution à l'aide de la classe <xref:System.Reflection.Emit.DynamicMethod>, et les exécuter à l'aide de délégués.  
  
- Définir des assemblys au moment de l'exécution, puis les exécuter et/ou les enregistrer sur disque.  
  
- Définir des assemblys au moment de l'exécution, les exécuter, puis les décharger et autoriser le garbage collection à libérer leurs ressources.  
  
- Définir des modules dans de nouveaux assemblys au moment de l'exécution, puis les exécuter et/ou les enregistrer sur disque.  
  
- Définir des types dans des modules au moment de l'exécution, créer des instances de ces types et appeler leurs méthodes.  
  
- Définir des informations symboliques pour des modules définis, qui peut être utilisées par des outils comme des débogueurs et des profileurs de code.  
  
En plus des types managés dans l’espace de noms <xref:System.Reflection.Emit>, il existe des interfaces de métadonnées non managées qui sont décrites dans la documentation de référence [Interfaces de métadonnées](../unmanaged-api/metadata/metadata-interfaces.md). L'émission de réflexion managée offre une vérification des erreurs sémantiques plus puissante et un niveau d'abstraction des métadonnées plus élevé que les interfaces de métadonnées non managées.  
  
Une autre ressource utile pour travailler avec les métadonnées et MSIL est la documentation de la Common Language Infrastructure (CLI), en particulier "Partie II : définition et sémantique des métadonnées" et "Partie III : jeu d'instructions de CIL". La documentation est disponible en ligne sur le [site Web d’Ecma](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="in-this-section"></a>Dans cette section
  
[Les questions de sécurité dans la réflexion émettent](security-issues-in-reflection-emit.md)  
Décrit les problèmes de sécurité liés à la création d'assemblys dynamiques en utilisant l'émission de réflexion.  

[Comment : Définir et exécuter des méthodes dynamiques](how-to-define-and-execute-dynamic-methods.md) Montre comment exécuter une méthode dynamique simple et une méthode dynamique liée à une instance d’une classe.

[Comment : Définir un type générique avec l’émission de réflexion](how-to-define-a-generic-type-with-reflection-emit.md) Montre comment créer un type générique simple avec deux paramètres de type, comment appliquer la classe, l’interface, et des contraintes spéciales aux paramètres de type, et comment créer des membres qui utilisent les paramètres de type de la classe comme types de paramètres et de types de retour.

[Comment : Définir une méthode générique avec l’émission de réflexion](how-to-define-a-generic-method-with-reflection-emit.md) Montre comment créer, émettre et invoquer une méthode générique simple.

[Assemblages collectibles pour la génération de type dynamique](collectible-assemblies.md) Introduit des assemblages de collection, qui sont des assemblages dynamiques qui peuvent être déchargés sans décharger le domaine d’application dans lequel ils ont été créés.
  
## <a name="reference"></a>Informations de référence  

<xref:System.Reflection.Emit.OpCodes>  
Répertorie les codes des instructions MSIL que vous pouvez utiliser pour créer des corps de méthode.  
  
<xref:System.Reflection.Emit>  
Contient des classes managées utilisées pour émettre des méthodes, des assemblys et des types dynamiques.  
  
<xref:System.Type>  
Décrit la classe <xref:System.Type>, qui représente des types dans la réflexion managée et dans l'émission de réflexion, et qui est essentielle dans l'utilisation de ces technologies.  
  
<xref:System.Reflection>  
Contient des classes managées utilisées pour explorer les métadonnées et le code managé.  
  
## <a name="related-sections"></a>Sections connexes  

[Réflexion](reflection.md)  
Explique comment explorer les métadonnées et le code managé.  
  
[Assemblys dans .NET](../../standard/assembly/index.md)  
Fournit une vue d’ensemble des assemblys dans les implémentations de .NET.
