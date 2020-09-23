---
title: Utilisation d'objets dynamiques
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 45f8b5c327d40f93b59c2115c75b3b7d385f5a8d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91057921"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Utilisation d'objets dynamiques (Visual Basic)

Les objets dynamiques offrent une autre méthode, autre que le `Object` type, pour effectuer une liaison tardive à un objet au moment de l’exécution. Un objet dynamique expose des membres tels que des propriétés et des méthodes au moment de l’exécution à l’aide d’interfaces dynamiques qui sont définies dans l' <xref:System.Dynamic> espace de noms. Vous pouvez utiliser les classes de l' <xref:System.Dynamic> espace de noms pour créer des objets qui fonctionnent avec des structures de données qui ne correspondent pas à un type ou un format statique. Vous pouvez également utiliser les objets dynamiques définis dans des langages dynamiques tels que IronPython et IronRuby. Pour obtenir des exemples qui montrent comment créer des objets dynamiques ou utiliser un objet dynamique défini dans un langage dynamique, consultez [procédure pas à pas : création et utilisation d’objets dynamiques](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject> ou <xref:System.Dynamic.ExpandoObject> .  
  
 Visual Basic crée une liaison avec des objets du Dynamic Language Runtime et des langages dynamiques tels qu’IronPython et IronRuby à l’aide de l' <xref:System.Dynamic.IDynamicMetaObjectProvider> interface. `IDynamicMetaObjectProvider`Les classes et sont des exemples de classes qui implémentent l’interface <xref:System.Dynamic.DynamicObject> <xref:System.Dynamic.ExpandoObject> .  
  
 Si un appel à liaison tardive est effectué vers un objet qui implémente l' `IDynamicMetaObjectProvider` interface, Visual Basic crée une liaison avec l’objet dynamique à l’aide de cette interface. Si un appel à liaison tardive est effectué vers un objet qui n’implémente pas l' `IDynamicMetaObjectProvider` interface, ou si l’appel à l' `IDynamicMetaObjectProvider` interface échoue, Visual Basic est lié à l’objet à l’aide des fonctionnalités de liaison tardive du runtime Visual Basic.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [Procédure pas à pas : création et utilisation d’objets dynamiques](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [Liaison précoce et tardive](index.md)
