---
ms.openlocfilehash: 4d410811095786b33580d25f6c6eab3ac2f27148
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616054"
---
### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a>La tâche ResolveAssemblyReference avertit désormais en cas de dépendances avec une architecture incorrecte

#### <a name="details"></a>Détails

La tâche émet un avertissement, MSB3270, qui indique qu’une référence ou l’une de ses dépendances ne correspond pas à l’architecture de l’application. Cette situation se produit, par exemple, si une application qui a été compilée avec l'option `AnyCPU` inclut une référence x86. Ainsi, l'application peut échouer au moment de l'exécution (si l'application est déployée en tant que processus x64 dans notre exemple).

#### <a name="suggestion"></a>Suggestion

Deux domaines sont impactés :

- La recompilation génère des avertissements qui n'étaient pas apparus quand l'application avait été compilée sous une version antérieure de MSBuild. En revanche, étant donné que l'avertissement identifie une source potentielle d'échec du runtime, vous devez l'examiner et le traiter.
- Si les avertissements sont considérés comme des erreurs, la compilation de l'application échouera.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.5.1       |
| Type    | Reciblage |
