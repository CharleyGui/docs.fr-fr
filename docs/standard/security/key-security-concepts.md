---
title: Concepts fondamentaux sur la sécurité
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- unauthorized access
- permissions [.NET Framework]
- security [.NET Framework], about security
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
ms.openlocfilehash: b7bcb7e56ca14d129eadcaeac19452d4a443713d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400658"
---
# <a name="key-security-concepts"></a>Concepts fondamentaux sur la sécurité
Le Microsoft .NET Framework offre la sécurité basée sur les rôles pour aider à résoudre les problèmes de sécurité relatifs au code mobile et pour permettre aux composants de déterminer ce que les utilisateurs sont autorisés à faire.  
  
## <a name="type-safety-and-security"></a>Sécurité de type et sécurité  
 Le code de type sécurisé accède uniquement aux emplacements de mémoire auxquels il est autorisé à accéder. (Pour cette discussion, la sécurité du type se réfère spécifiquement à la sécurité du type de mémoire et ne doit pas être confondue avec la sécurité de type à un égard plus large.) Par exemple, le code de type-sécurité ne peut pas lire les valeurs des champs privés d’un autre objet. Il accède aux types uniquement de manière autorisée et bien définie.  
  
 Pendant la compilation juste-à-temps (JIT, Just-In-Time), un processus de vérification facultatif examine les métadonnées et le Microsoft Intermediate Language (MSIL) d'une méthode devant subir une compilation JIT en code machine natif pour vérifier qu'ils sont de type sécurisé. Ce processus est omis si le code est autorisé à ignorer la vérification. Pour plus d’informations sur la vérification, consultez [Processus d’exécution managée](../../../docs/standard/managed-execution-process.md).  
  
 Bien que la vérification de sécurité de type ne soit pas obligatoire pour exécuter du code managé, la sécurité de type joue un rôle crucial dans l'isolation des assemblys et dans la mise en œuvre de la sécurité. Quand le code est de type sécurisé, le Common Language Runtime peut isoler totalement les assemblys les uns des autres. Cette isolation permet de s'assurer que les assemblys ne peuvent pas nuire les uns aux autres et augmente la fiabilité des applications. Les composants de type sécurisé peuvent s'exécuter en toute sécurité dans le même processus, même s'ils sont approuvés à différents niveaux. Quand le code n'est pas de type sécurisé, des effets secondaires indésirables peuvent se produire. Par exemple, le runtime ne peut pas empêcher du code managé d'appeler du code natif (non managé) et d'exécuter des opérations nuisibles. Quand le code est de type sécurisé, le mécanisme de sécurité du runtime garantit qu'il n'accède pas à du code natif, sauf s'il a l'autorisation de le faire. Tout le code qui n'est pas de type sécurisé ne peut s'exécuter que s'il a obtenu l'autorisation <xref:System.Security.Permissions.SecurityPermission> avec le membre d'énumération transmis <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A>.  
  
 Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="principal"></a>Principal  
 Un principal représente l'identité et le rôle d'un utilisateur et agit au nom de l'utilisateur. Dans .NET Framework, la sécurité basée sur les rôles prend en charge trois types de principaux :  
  
- Les principaux génériques représentent les utilisateurs et les rôles qui existent indépendamment des utilisateurs et des rôles Windows.  
  
- Les principaux Windows représentent les utilisateurs et les rôles Windows (ou leurs groupes Windows). Un principal Windows peut emprunter l'identité d'un autre utilisateur, ce qui signifie qu'il peut accéder à une ressource sous le nom d'un utilisateur tout en présentant l'identité de l'autre utilisateur.  
  
- Les principaux personnalisés peuvent être définis par une application, en fonction des besoins de celle-ci. Ils peuvent étendre les notions de base applicables à l'identité et aux rôles du principal.  
  
 Pour plus d’informations, consultez [Objets Principal et Identity](../../../docs/standard/security/principal-and-identity-objects.md).  
  
## <a name="authentication"></a>Authentication  
 Le processus d'authentification consiste à établir et à vérifier l'identité d'un principal en examinant les informations d'identification de l'utilisateur et en les validant auprès de l'autorité appropriée. Votre code peut utiliser directement les informations obtenues au cours de l'authentification. Vous pouvez également utiliser la sécurité basée sur les rôles du .NET Framework pour authentifier l'utilisateur actuel et déterminer s'il faut ou non autoriser ce principal à accéder à votre code. Consultez les surcharges de la méthode <xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=nameWithType> pour obtenir des exemples d'authentification du principal pour des rôles spécifiques. Par exemple, vous pouvez utiliser la surcharge <xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=nameWithType> pour déterminer si l'utilisateur actuel est membre du groupe Administrateurs.  
  
 De nombreux mécanismes d'authentification sont utilisés de nos jours et la majorité d'entre eux peuvent être utilisés avec la sécurité basée sur les rôles de .NET Framework. Parmi les mécanismes les plus courants figurent notamment Basic, Digest, Passport, les mécanismes liés aux systèmes d'exploitation (tels que NTLM ou Kerberos) ou encore ceux définis par les applications.  
  
### <a name="example"></a> Exemple  
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
 L'autorisation est le processus qui consiste à déterminer si un principal est autorisé à exécuter l'opération demandée. L'autorisation a lieu après l'authentification, et utilise les informations se rapportant à l'identité et aux rôles du principal pour déterminer les ressources auxquelles il peut avoir accès. Vous pouvez utiliser la sécurité basée sur les rôles de .NET Framework pour l'implémentation de l'autorisation.
