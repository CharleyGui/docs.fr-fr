---
ms.openlocfilehash: 768a948849064cedb38110f5ed271717442325c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620021"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a>Le nom du fichier journal créé par la méthode ObjectContext.CreateDatabase a été changé pour répondre aux spécifications SQL Server

#### <a name="details"></a>Détails

Quand la méthode <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> est appelée directement ou en utilisant Code First avec le fournisseur SqlClient et une valeur AttachDBFilename dans la chaîne de connexion, elle crée un fichier journal nommé nom_fichier_log.ldf au lieu de nom_fichier.ldf (où « nom_fichier » correspond au nom du fichier spécifié par la valeur AttachDBFilename). Cette modification améliore le débogage en fournissant un fichier journal dont le nom répond aux spécifications SQL Server.

#### <a name="suggestion"></a>Suggestion

Si le nom du fichier journal est important pour une application, celle-ci doit être mise à jour pour attendre le format de nom de fichier standard « _log.ldf ».

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
