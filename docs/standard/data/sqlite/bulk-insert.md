---
title: Insertion en bloc
ms.date: 12/13/2019
description: Conseils sur les performances que vous pouvez utiliser lorsque vous apportez de nombreuses modifications à la base de données.
ms.openlocfilehash: 9d87d5c8d70f8e70479f9aa02b7802f73b88de9e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447040"
---
# <a name="bulk-insert"></a>Insertion en bloc

SQLite n’a pas de méthode spéciale pour insérer des données en bloc. Pour obtenir des performances optimales lors de l’insertion ou de la mise à jour de données, assurez-vous d’effectuer les opérations suivantes :

- Utilisez une transaction.
- Réutilisez la même commande paramétrable. Les exécutions suivantes réutiliseront la compilation du premier.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BulkInsertSample/Program.cs?name=snippet_BulkInsert)]
