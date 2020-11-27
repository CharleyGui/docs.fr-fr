---
title: Types déconseillés dans Windows Workflow Foundation
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: 628963650d32237dedbb6ab2a0a2d9a79866af18
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272870"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a>Types déconseillés dans Windows Workflow Foundation

Dans le .NET 4, l’équipe de workflow a mis à disposition un nouveau au moteur de workflow dans l’espace de noms <xref:System.Activities>. Avec la version de .NET Framework 4,5 bêta, nous indiquons la plupart des types dans les espaces de noms « WF 3 » <xref:System.Workflow.Activities> , <xref:System.Workflow.ComponentModel> et  <xref:System.Workflow.Runtime> comme obsolètes.

## <a name="obsolete-namespaces-and-tools"></a>Espaces de noms et outils obsolètes

 Les assemblys suivants ont un ou plusieurs types publics qui seront déconseillés :

- System.Workflow.Activities.dll

- System.Workflow.ComponentModel.dll

- System.Workflow.Runtime.dll

- System.WorkflowServices.dll

- Microsoft.Workflow.DebugController.dll

- Microsoft.Workflow.Compiler.exe

- Wfc.exe

 Par conséquent, les clients qui utilisent les API WF 3 déconseillées rencontreront des avertissements de génération avec un message similaire au suivant :

 **AVERTISSEMENT BC40000 : X est obsolète : les types WF 3 sont déconseillés. Utilisez WF 4 à la place.** Nous allons supprimer les types du .NET Framework dans une mise en production ultérieure, mais nous n’avons pas encore déterminé cette plage de temps (pas dans la version 4.5). Cette étape nous permet de communiquer notre direction à nos clients et leur laisse le temps de migrer vers le nouveau modèle WF4. Nous allons, bien sûr, continuer à prendre en charge ces types WF 3 dans le cadre de la [stratégie de cycle de vie support Microsoft](/lifecycle/). Les applications WF3 existantes s’exécutent sans problème sur .NET Framework 4,5 et Visual Studio 2012 prend en charge les solutions basées sur WF3 nouvelles et existantes.

 Les types liés aux règles dans l'espace de noms <xref:System.Workflow.Activities.Rules>, qui n'ont pas été remplacés dans WF 4.5, n'ont pas été déconseillés.

 Les clients qui souhaitent migrer leurs applications vers WF 4 trouveront de l’aide dans les [instructions de migration de workflow 4](migration-guidance.md).
