---
title: 'Procédure : restreindre l’accès à la classe PrincipalPermissionAttribute'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
ms.openlocfilehash: 92d27548c510a19bf36ffaffb532f48461146d99
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269611"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a><span data-ttu-id="71189-102">Procédure : restreindre l’accès à la classe PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="71189-102">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>

<span data-ttu-id="71189-103">Le contrôle de l'accès aux ressources sur un ordinateur de domaine Windows est une tâche de sécurité de base.</span><span class="sxs-lookup"><span data-stu-id="71189-103">Controlling the access to resources on a Windows-domain computer is a basic security task.</span></span> <span data-ttu-id="71189-104">Par exemple, certains utilisateurs doivent pouvoir consulter des données sensibles, telles que les informations relatives aux salaires.</span><span class="sxs-lookup"><span data-stu-id="71189-104">For example, only certain users should be able to view sensitive data, such as payroll information.</span></span> <span data-ttu-id="71189-105">Cette rubrique explique comment restreindre l'accès à une méthode en exigeant que l'utilisateur appartienne à un groupe prédéfini.</span><span class="sxs-lookup"><span data-stu-id="71189-105">This topic explains how to restrict access to a method by demanding that the user belong to a predefined group.</span></span> <span data-ttu-id="71189-106">Pour obtenir un exemple fonctionnel, consultez [autorisation de l’accès aux opérations de service](./samples/authorizing-access-to-service-operations.md).</span><span class="sxs-lookup"><span data-stu-id="71189-106">For a working sample, see [Authorizing Access to Service Operations](./samples/authorizing-access-to-service-operations.md).</span></span>  
  
 <span data-ttu-id="71189-107">La tâche se compose de deux procédures séparées.</span><span class="sxs-lookup"><span data-stu-id="71189-107">The task consists of two separate procedures.</span></span> <span data-ttu-id="71189-108">La première crée le groupe et le remplit avec les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="71189-108">The first creates the group and populates it with users.</span></span> <span data-ttu-id="71189-109">La deuxième applique la classe <xref:System.Security.Permissions.PrincipalPermissionAttribute> pour spécifier le groupe.</span><span class="sxs-lookup"><span data-stu-id="71189-109">The second applies the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to specify the group.</span></span>  
  
### <a name="to-create-a-windows-group"></a><span data-ttu-id="71189-110">Pour créer un groupe Windows</span><span class="sxs-lookup"><span data-stu-id="71189-110">To create a Windows group</span></span>  
  
1. <span data-ttu-id="71189-111">Ouvrez la console de gestion de l' **ordinateur** .</span><span class="sxs-lookup"><span data-stu-id="71189-111">Open the **Computer Management** console.</span></span>  
  
2. <span data-ttu-id="71189-112">Dans le volet gauche, cliquez sur **utilisateurs et groupes locaux**.</span><span class="sxs-lookup"><span data-stu-id="71189-112">In the left panel, click **Local Users and Groups**.</span></span>  
  
3. <span data-ttu-id="71189-113">Cliquez avec le bouton droit sur **groupes**, puis cliquez sur **nouveau groupe**.</span><span class="sxs-lookup"><span data-stu-id="71189-113">Right-click **Groups**, and click **New Group**.</span></span>  
  
4. <span data-ttu-id="71189-114">Dans la zone **nom du groupe** , tapez un nom pour le nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="71189-114">In the **Group Name** box, type a name for the new group.</span></span>  
  
5. <span data-ttu-id="71189-115">Dans la zone **Description** , tapez une description du nouveau groupe.</span><span class="sxs-lookup"><span data-stu-id="71189-115">In the **Description** box, type a description of the new group.</span></span>  
  
6. <span data-ttu-id="71189-116">Cliquez sur le bouton **Ajouter** pour ajouter de nouveaux membres au groupe.</span><span class="sxs-lookup"><span data-stu-id="71189-116">Click the **Add** button to add new members to the group.</span></span>  
  
7. <span data-ttu-id="71189-117">Si vous vous êtes vous-même ajouté au groupe et souhaitez tester le code suivant, vous devez vous déconnecter, puis vous reconnecter à l'ordinateur pour être inclus dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="71189-117">If you have added yourself to the group and want to test the following code, you must log off the computer and log back on to be included in the group.</span></span>  
  
### <a name="to-demand-user-membership"></a><span data-ttu-id="71189-118">Pour demander l'appartenance des utilisateurs</span><span class="sxs-lookup"><span data-stu-id="71189-118">To demand user membership</span></span>  
  
1. <span data-ttu-id="71189-119">Ouvrez le fichier de code Windows Communication Foundation (WCF) qui contient le code de contrat de service implémenté.</span><span class="sxs-lookup"><span data-stu-id="71189-119">Open the Windows Communication Foundation (WCF) code file that contains the implemented service contract code.</span></span> <span data-ttu-id="71189-120">Pour plus d’informations sur l’implémentation d’un contrat, consultez [implémentation de contrats de service](implementing-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="71189-120">For more information about implementing a contract, see [Implementing Service Contracts](implementing-service-contracts.md).</span></span>  
  
2. <span data-ttu-id="71189-121">Appliquez l'attribut <xref:System.Security.Permissions.PrincipalPermissionAttribute> à chaque méthode qui doit être restreinte à un groupe spécifique.</span><span class="sxs-lookup"><span data-stu-id="71189-121">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to each method that must be restricted to a specific group.</span></span> <span data-ttu-id="71189-122">Affectez <xref:System.Security.Permissions.SecurityAttribute.Action%2A> à la propriété <xref:System.Security.Permissions.SecurityAction.Demand> et le nom du groupe à la propriété <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>.</span><span class="sxs-lookup"><span data-stu-id="71189-122">Set the <xref:System.Security.Permissions.SecurityAttribute.Action%2A> property to <xref:System.Security.Permissions.SecurityAction.Demand> and the <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> property to the name of the group.</span></span> <span data-ttu-id="71189-123">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="71189-123">For example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="71189-124">Si vous appliquez l'attribut <xref:System.Security.Permissions.PrincipalPermissionAttribute> à un contrat, une exception <xref:System.Security.SecurityException> sera levée.</span><span class="sxs-lookup"><span data-stu-id="71189-124">If you apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a contract a <xref:System.Security.SecurityException> will be thrown.</span></span> <span data-ttu-id="71189-125">Vous pouvez appliquer l'attribut uniquement au niveau de la méthode.</span><span class="sxs-lookup"><span data-stu-id="71189-125">You can only apply the attribute at the method level.</span></span>  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a><span data-ttu-id="71189-126">Utilisation d'un certificat pour contrôler l'accès à une méthode</span><span class="sxs-lookup"><span data-stu-id="71189-126">Using a Certificate to Control Access to a Method</span></span>  

 <span data-ttu-id="71189-127">Vous pouvez également utiliser la classe `PrincipalPermissionAttribute` pour contrôler l'accès à une méthode si le type d'informations d'identification du client est un certificat.</span><span class="sxs-lookup"><span data-stu-id="71189-127">You can also use the `PrincipalPermissionAttribute` class to control access to a method if the client credential type is a certificate.</span></span> <span data-ttu-id="71189-128">Pour ce faire, vous devez avoir l'empreinte numérique et le sujet du certificat.</span><span class="sxs-lookup"><span data-stu-id="71189-128">To do this, you must have the certificate's subject and thumbprint.</span></span>  
  
 <span data-ttu-id="71189-129">Pour examiner les propriétés d’un certificat, consultez [Comment : afficher des certificats avec le composant logiciel enfichable MMC](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="71189-129">To examine a certificate for its properties, see [How to: View Certificates with the MMC Snap-in](./feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span> <span data-ttu-id="71189-130">Pour trouver la valeur de l’empreinte numérique, consultez [Comment : récupérer l’empreinte numérique d’un certificat](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="71189-130">To find the thumbprint value, see [How to: Retrieve the Thumbprint of a Certificate](./feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
#### <a name="to-control-access-using-a-certificate"></a><span data-ttu-id="71189-131">Pour contrôler l'accès à l'aide d'un certificat</span><span class="sxs-lookup"><span data-stu-id="71189-131">To control access using a certificate</span></span>  
  
1. <span data-ttu-id="71189-132">Appliquez la classe <xref:System.Security.Permissions.PrincipalPermissionAttribute> à la méthode à laquelle vous souhaitez restreindre l'accès.</span><span class="sxs-lookup"><span data-stu-id="71189-132">Apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> class to the method you want to restrict access to.</span></span>  
  
2. <span data-ttu-id="71189-133">Affectez <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType> à l'action de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="71189-133">Set the action of the attribute to <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.</span></span>  
  
3. <span data-ttu-id="71189-134">Affectez à la propriété `Name` une chaîne qui se compose du nom du sujet et de l'empreinte numérique du certificat.</span><span class="sxs-lookup"><span data-stu-id="71189-134">Set the `Name` property to a string that consists of the subject name and the certificate's thumbprint.</span></span> <span data-ttu-id="71189-135">Séparez les deux valeurs par un point-virgule et un espace, tel qu'indiqué dans l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="71189-135">Separate the two values with a semicolon and a space, as shown in the following example:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. <span data-ttu-id="71189-136">Affectez <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> à la propriété <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, tel qu'indiqué dans l'exemple de configuration suivant :</span><span class="sxs-lookup"><span data-stu-id="71189-136">Set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> as shown in the following configuration example:</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="71189-137">L'affectation de `UseAspNetRoles` à cette valeur indique que la propriété `Name` de `PrincipalPermissionAttribute` sera utilisée pour effectuer une comparaison de chaînes.</span><span class="sxs-lookup"><span data-stu-id="71189-137">Setting this value to `UseAspNetRoles` indicates that the `Name` property of the `PrincipalPermissionAttribute` will be used to perform a string comparison.</span></span> <span data-ttu-id="71189-138">Lorsqu’un certificat est utilisé comme informations d’identification du client, par défaut, WCF concatène le nom commun du certificat et l’empreinte numérique avec un point-virgule pour créer une valeur unique pour l’identité principale du client.</span><span class="sxs-lookup"><span data-stu-id="71189-138">When a certificate is used as a client credential, by default WCF concatenates the certificate common name and the thumbprint with a semicolon to create a unique value for the client's primary identity.</span></span> <span data-ttu-id="71189-139">Avec `UseAspNetRoles` défini en tant que `PrincipalPermissionMode` sur le service, la valeur de cette identité principale est comparée à celle de la propriété `Name` afin de déterminer les droits d'accès de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="71189-139">With `UseAspNetRoles` set as the `PrincipalPermissionMode` on the service, this primary identity value is compared with the `Name` property value to determine the access rights of the user.</span></span>  
  
     <span data-ttu-id="71189-140">Vous pouvez également, lorsque vous créez un service auto-hébergé, définir la propriété <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> dans le code, tel qu'indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="71189-140">Alternatively, when creating a self-hosted service, set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property in code as shown in the following code:</span></span>  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="71189-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71189-141">See also</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [<span data-ttu-id="71189-142">Authorizing Access to Service Operations</span><span class="sxs-lookup"><span data-stu-id="71189-142">Authorizing Access to Service Operations</span></span>](./samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="71189-143">Présentation de la sécurité</span><span class="sxs-lookup"><span data-stu-id="71189-143">Security Overview</span></span>](./feature-details/security-overview.md)
- [<span data-ttu-id="71189-144">Implémentation de contrats de service</span><span class="sxs-lookup"><span data-stu-id="71189-144">Implementing Service Contracts</span></span>](implementing-service-contracts.md)
