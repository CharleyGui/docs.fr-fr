---
title: Concepts fondamentaux sur la sécurité
ms.date: 07/15/2020
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- unauthorized access
- permissions [.NET]
- security [.NET], about security
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
ms.openlocfilehash: a9f0703217b55c90c4e98503402d3fbf60a45ea7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831063"
---
# <a name="key-security-concepts"></a>Concepts fondamentaux sur la sécurité

> [!NOTE]
> Cet article s’applique à Windows.
>
> Pour plus d’informations sur la ASP.NET Core, consultez [vue d’ensemble de la sécurité ASP.net Core](/aspnet/core/security/).

.NET offre une sécurité basée sur les rôles pour aider à résoudre les problèmes de sécurité liés au code mobile et à fournir une prise en charge permettant aux composants de déterminer ce que les utilisateurs sont autorisés à faire.  
  
## <a name="type-safety-and-security"></a>Sécurité de type et sécurité  

Le code de type sécurisé accède uniquement aux emplacements de mémoire auxquels il est autorisé à accéder. (Pour cette discussion, la sécurité de type fait spécifiquement référence à la sécurité de type de la mémoire et ne doit pas être confondue avec la sécurité de type dans un respect plus large.) Par exemple, le code de type sécurisé ne peut pas lire les valeurs des champs privés d’un autre objet. Il accède aux types uniquement de manière autorisée et bien définie.  
  
Pendant la compilation juste-à-temps (JIT, Just-In-Time), un processus de vérification facultatif examine les métadonnées et le Microsoft Intermediate Language (MSIL) d'une méthode devant subir une compilation JIT en code machine natif pour vérifier qu'ils sont de type sécurisé. Ce processus est omis si le code est autorisé à ignorer la vérification. Pour plus d’informations sur la vérification, consultez [Processus d’exécution managée](../managed-execution-process.md).  
  
Bien que la vérification de sécurité de type ne soit pas obligatoire pour exécuter du code managé, la sécurité de type joue un rôle crucial dans l'isolation des assemblys et dans la mise en œuvre de la sécurité. Quand le code est de type sécurisé, le Common Language Runtime peut isoler totalement les assemblys les uns des autres. Cette isolation permet de s'assurer que les assemblys ne peuvent pas nuire les uns aux autres et augmente la fiabilité des applications. Les composants de type sécurisé peuvent s'exécuter en toute sécurité dans le même processus, même s'ils sont approuvés à différents niveaux. Quand le code n'est pas de type sécurisé, des effets secondaires indésirables peuvent se produire. Par exemple, le runtime ne peut pas empêcher du code managé d'appeler du code natif (non managé) et d'exécuter des opérations nuisibles. Quand le code est de type sécurisé, le mécanisme de sécurité du runtime garantit qu'il n'accède pas à du code natif, sauf s'il a l'autorisation de le faire. Tout le code qui n'est pas de type sécurisé ne peut s'exécuter que s'il a obtenu l'autorisation <xref:System.Security.Permissions.SecurityPermission> avec le membre d'énumération transmis <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A>.  
  
Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../framework/misc/code-access-security-basics.md).  
  
## <a name="principal"></a>Principal  

Un principal représente l'identité et le rôle d'un utilisateur et agit au nom de l'utilisateur. La sécurité basée sur les rôles dans .NET prend en charge trois types de principaux :  
  
- Les principaux génériques représentent les utilisateurs et les rôles qui existent indépendamment des utilisateurs et des rôles Windows.  
  
- Les principaux Windows représentent les utilisateurs et les rôles Windows (ou leurs groupes Windows). Un principal Windows peut emprunter l'identité d'un autre utilisateur, ce qui signifie qu'il peut accéder à une ressource sous le nom d'un utilisateur tout en présentant l'identité de l'autre utilisateur.  
  
- Les principaux personnalisés peuvent être définis par une application, en fonction des besoins de celle-ci. Ils peuvent étendre les notions de base applicables à l'identité et aux rôles du principal.  
  
Pour plus d’informations, consultez [Objets Principal et Identity](principal-and-identity-objects.md).  
  
## <a name="authentication"></a>Authentification  
Le processus d'authentification consiste à établir et à vérifier l'identité d'un principal en examinant les informations d'identification de l'utilisateur et en les validant auprès de l'autorité appropriée. Votre code peut utiliser directement les informations obtenues au cours de l'authentification. Vous pouvez également utiliser la sécurité basée sur les rôles .NET pour authentifier l’utilisateur actuel et déterminer s’il faut autoriser ce principal à accéder à votre code. Consultez les surcharges de la méthode <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> pour obtenir des exemples d'authentification du principal pour des rôles spécifiques. Par exemple, vous pouvez utiliser la surcharge <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> pour déterminer si l'utilisateur actuel est membre du groupe Administrateurs.  
  
Un grand nombre de mécanismes d’authentification sont utilisés aujourd’hui, dont la plupart peuvent être utilisés avec la sécurité basée sur les rôles .NET. Parmi les mécanismes les plus courants figurent notamment Basic, Digest, Passport, les mécanismes liés aux systèmes d'exploitation (tels que NTLM ou Kerberos) ou encore ceux définis par les applications.  
  
### <a name="example"></a>Exemple  

L'exemple suivant nécessite que le principal actif soit un administrateur. Le paramètre `name` est `null`, qui autorise tout utilisateur ayant la qualité d'administrateur à passer la demande.  
  
> [!NOTE]
> Dans Windows Vista, le contrôle de compte d'utilisateur détermine les privilèges d'un utilisateur. Si vous êtes membre du groupe Administrateurs intégrés, deux jetons d'accès au moment de l'exécution vous sont assignés : un jeton d'accès utilisateur standard et un jeton d'accès administrateur. Par défaut, vous êtes dans le rôle d'utilisateur standard. Pour exécuter le code nécessitant que vous soyez administrateur, vous devez d'abord élever vos privilèges d'utilisateur standard à administrateur. Vous pouvez effectuer cela au démarrage d'une application en cliquant avec le bouton droit sur l'icône de l'application et en indiquant que vous voulez l'exécuter en tant qu'administrateur.  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 L'exemple suivant montre comment déterminer l'identité du principal et les rôles disponibles pour celui-ci. Une application de cet exemple peut consister à confirmer que le rôle de l'utilisateur actuel l'autorise à utiliser votre application.  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## <a name="authorization"></a>Autorisation  

L'autorisation est le processus qui consiste à déterminer si un principal est autorisé à exécuter l'opération demandée. L'autorisation a lieu après l'authentification, et utilise les informations se rapportant à l'identité et aux rôles du principal pour déterminer les ressources auxquelles il peut avoir accès. Vous pouvez utiliser la sécurité basée sur les rôles .NET pour implémenter l’autorisation.

## <a name="see-also"></a>Voir aussi

- [Sécurité ASP.NET Core](/aspnet/core/security/)
