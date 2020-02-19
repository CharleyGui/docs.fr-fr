---
title: Signature de procédures stockées dans SQL Server
ms.date: 01/05/2018
ms.assetid: eeed752c-0084-48e5-9dca-381353007a0d
ms.openlocfilehash: 0131655d06a6ef543ea460d04739401538cac04b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452355"
---
# <a name="signing-stored-procedures-in-sql-server"></a>Signature de procédures stockées dans SQL Server

Une signature numérique est un condensé de données chiffrées avec la clé privée du signataire. La clé privée garantit que la signature numérique est la propriété unique de son détenteur ou propriétaire. Vous pouvez signer des procédures stockées, des fonctions (à l’exception des fonctions table incluses), des déclencheurs et des assemblys.

Vous pouvez signer une procédure stockée avec un certificat ou une clé asymétrique. Cela est très utile lorsque des autorisations ne peuvent pas être héritées par le biais du chaînage des propriétés ou lorsque ce dernier est rompu, comme avec SQL dynamique. Vous pouvez ensuite créer un utilisateur mappé au certificat, en accordant au certificat des autorisations d’utilisateur sur les objets auxquels la procédure stockée doit accéder.

Vous pouvez également créer une connexion mappée sur le même certificat, puis accorder les autorisations de niveau serveur nécessaires à cette connexion, ou ajouter la connexion à un ou plusieurs rôles serveur fixes. Cela est conçu pour éviter d’activer le paramètre de base de données `TRUSTWORTHY` pour les scénarios dans lesquels des autorisations de niveau supérieur sont nécessaires.

Lorsque la procédure stockée est exécutée, SQL Server associe les autorisations de l’utilisateur et/ou de la connexion du certificat à celles de l’appelant. Contrairement à la clause `EXECUTE AS`, elle ne modifie pas le contexte d’exécution de la procédure. Les fonctions intégrées qui retournent les noms d'accès et d'utilisateur retournent le non de l'appelant, et non celui de l'utilisateur du certificat.

## <a name="creating-certificates"></a>Création de certificats

Lorsque vous signez une procédure stockée avec un certificat ou une clé asymétrique, un résumé des données composé du hachage chiffré du code de la procédure stockée, ainsi que de l’utilisateur Execute-As, est créé à l’aide de la clé privée. Au moment de l’exécution, le condensat des données est chiffré avec la clé publique et comparée à la valeur de hachage de la procédure stockée. La modification de l’utilisateur Execute-As invalide la valeur de hachage afin que la signature numérique ne corresponde plus. La modification de la procédure stockée supprime entièrement la signature, ce qui empêche une personne qui n’a pas accès à la clé privée de modifier le code de la procédure stockée. Dans les deux cas, vous devez signer à nouveau la procédure chaque fois que vous modifiez le code ou l’utilisateur exécuter en tant que.

Deux étapes sont nécessaires pour la signature d’un module :

1. Créez un certificat à l'aide de l'instruction Transact-SQL `CREATE CERTIFICATE [certificateName]`. Cette instruction possède plusieurs options permettant de définir une date de début et de fin, de même qu'un mot de passe. La date d’expiration par défaut est d’un an.

1. Signez la procédure avec le certificat en utilisant l'instruction Transact-SQL `ADD SIGNATURE TO [procedureName] BY CERTIFICATE [certificateName]`.

Une fois le module signé, vous devez créer un ou plusieurs principaux afin de conserver les autorisations supplémentaires qui doivent être associées au certificat.

Si le module a besoin d’autorisations supplémentaires au niveau de la base de données :

1. Créez un utilisateur de base de données associé à ce certificat à l'aide de l'instruction Transact-SQL `CREATE USER [userName] FROM CERTIFICATE [certificateName]`. Cet utilisateur existe uniquement dans la base de données et n’est pas associé à une connexion, sauf si un compte de connexion a été créé à partir de ce même certificat.

1. Accordez à l’utilisateur du certificat les autorisations requises au niveau de la base de données.

Si le module a besoin d’autorisations supplémentaires au niveau du serveur :

1. Copiez le certificat dans la base de données `master`.

1. Créez une connexion associée à ce certificat à l’aide de l’instruction Transact-SQL `CREATE LOGIN [userName] FROM CERTIFICATE [certificateName]`.

1. Accordez au certificat de connexion les autorisations requises au niveau du serveur.

> [!NOTE]
> Un certificat ne permet pas d'accorder des autorisations à un utilisateur dont les autorisations ont été révoquées à l'aide de l'instruction DENY. L'instruction DENY a toujours priorité sur l'instruction GRANT, ce qui empêche l'appelant d'hériter des autorisations accordées à l'utilisateur du certificat.

## <a name="external-resources"></a>Ressources externes

Pour plus d'informations, consultez les ressources ci-dessous.

|Ressource|Description|
|--------------|-----------------|
|[Signature de module](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms345102(v=sql.100))|Décrit la signature de module, en fournissant un exemple de scénario et des liens vers les articles Transact-SQL pertinents.|
|[Signature de procédures stockées à l’aide d’un certificat](/sql/relational-databases/tutorial-signing-stored-procedures-with-a-certificate)|Propose un didacticiel de signature d'une procédure stockée à l'aide d'un certificat.|

## <a name="see-also"></a>Voir aussi

- [Sécurisation des applications ADO.NET](../securing-ado-net-applications.md)
- [Vue d’ensemble de la sécurité SQL Server](overview-of-sql-server-security.md)
- [Scénarios de sécurité des applications dans SQL Server](application-security-scenarios-in-sql-server.md)
- [Gestion des autorisations avec les procédures stockées dans SQL Server](managing-permissions-with-stored-procedures-in-sql-server.md)
- [Écriture d’une instruction SQL dynamique sécurisée dans SQL Server](writing-secure-dynamic-sql-in-sql-server.md)
- [Personnalisation des autorisations avec l’emprunt d’identité dans SQL Server](customizing-permissions-with-impersonation-in-sql-server.md)
- [Modification des données avec les procédures stockées](../modifying-data-with-stored-procedures.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
