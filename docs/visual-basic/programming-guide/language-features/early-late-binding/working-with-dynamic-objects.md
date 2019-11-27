---
title: Utilisation d'objets dynamiques
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic objects [Visual Basic]
ms.assetid: bdee2a00-07ff-46f9-86dd-fdac9b99cc97
ms.openlocfilehash: 20d007fb48e1db352bab6d8e25d2e60e02554732
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345173"
---
# <a name="working-with-dynamic-objects-visual-basic"></a>Utilisation d'objets dynamiques (Visual Basic)
Les objets dynamiques offrent une autre méthode, autre que le type de `Object`, pour une liaison tardive à un objet au moment de l’exécution. Un objet dynamique expose des membres tels que des propriétés et des méthodes au moment de l’exécution à l’aide d’interfaces dynamiques qui sont définies dans l’espace de noms <xref:System.Dynamic>. Vous pouvez utiliser les classes de l’espace de noms <xref:System.Dynamic> pour créer des objets qui fonctionnent avec des structures de données qui ne correspondent pas à un type ou un format statique. Vous pouvez également utiliser les objets dynamiques définis dans des langages dynamiques tels que IronPython et IronRuby. Pour obtenir des exemples qui montrent comment créer des objets dynamiques ou utiliser un objet dynamique défini dans un langage dynamique, consultez [procédure pas à pas : création et utilisation d’objets dynamiques](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md), <xref:System.Dynamic.DynamicObject>ou <xref:System.Dynamic.ExpandoObject>.  
  
 Visual Basic crée une liaison avec des objets du Dynamic Language Runtime et des langages dynamiques tels qu’IronPython et IronRuby à l’aide de l’interface <xref:System.Dynamic.IDynamicMetaObjectProvider>. Les classes <xref:System.Dynamic.DynamicObject> et <xref:System.Dynamic.ExpandoObject> sont des exemples de classes qui implémentent l’interface `IDynamicMetaObjectProvider`.  
  
 Si un appel à liaison tardive est effectué vers un objet qui implémente l’interface `IDynamicMetaObjectProvider`, Visual Basic crée une liaison avec l’objet dynamique à l’aide de cette interface. Si un appel à liaison tardive est effectué vers un objet qui n’implémente pas l’interface `IDynamicMetaObjectProvider`, ou si l’appel à l’interface `IDynamicMetaObjectProvider` échoue, Visual Basic crée une liaison avec l’objet à l’aide des fonctionnalités de liaison tardive de l’Visual Basic Runtime.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Dynamic.DynamicObject>
- <xref:System.Dynamic.ExpandoObject>
- [Procédure pas à pas : création et utilisation d’objets dynamiques](../../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
- [Liaison anticipée et liaison tardive](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
