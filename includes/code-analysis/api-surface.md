---
ms.openlocfilehash: bf7ea8a36b9c36d82b4c00ada890829bf4c2c024
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "97700856"
---
### <a name="include-specific-api-surfaces"></a>Inclure des surfaces d’API spécifiques

Vous pouvez configurer les parties de votre code base pour exécuter cette règle, en fonction de leur accessibilité. Par exemple, pour spécifier que la règle doit s’exécuter uniquement sur la surface d’API non publique, ajoutez la paire clé-valeur suivante à un fichier *. editorconfig* dans votre projet :

```ini
dotnet_code_quality.CAXXXX.api_surface = private, internal
```
