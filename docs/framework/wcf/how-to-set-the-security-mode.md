---
title: 'Comment : définir le mode de sécurité'
description: 'Découvrez comment définir les trois modes de sécurité WCF courants sur la plupart des liaisons prédéfinies : transport, message et TransportWithMessageCredential.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
ms.openlocfilehash: 2f834e1930b7676592f6cbc29a577424d75ebc01
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244541"
---
# <a name="how-to-set-the-security-mode"></a><span data-ttu-id="e31a1-103">Comment : définir le mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="e31a1-103">How to: Set the Security Mode</span></span>

<span data-ttu-id="e31a1-104">La sécurité Windows Communication Foundation (WCF) a trois modes de sécurité communs qui se trouvent sur la plupart des liaisons prédéfinies : transport, message et transport avec informations d’identification de message.</span><span class="sxs-lookup"><span data-stu-id="e31a1-104">Windows Communication Foundation (WCF) security has three common security modes that are found on most predefined bindings: transport, message, and "transport with message credential."</span></span> <span data-ttu-id="e31a1-105">Il existe également deux modes supplémentaires propres à deux liaisons particulières. Il s’agit du mode « informations d’identification de transport uniquement » disponible sur la liaison <xref:System.ServiceModel.BasicHttpBinding> et du mode « les deux » disponible sur la liaison <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="e31a1-105">Two additional modes are specific to two bindings: the "transport-credential only" mode found on the <xref:System.ServiceModel.BasicHttpBinding>, and the "Both" mode, found on the <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="e31a1-106">Cette rubrique traite essentiellement des trois principaux modes de sécurité : <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message> et <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="e31a1-106">However, this topic concentrates on the three common security modes: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, and <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>

<span data-ttu-id="e31a1-107">Remarque : toutes les liaisons prédéfinies ne prennent pas nécessairement en charge chacun de ces modes.</span><span class="sxs-lookup"><span data-stu-id="e31a1-107">Note that not every predefined binding supports all of these modes.</span></span> <span data-ttu-id="e31a1-108">Cette rubrique, dans laquelle le mode est défini à l'aide des classes <xref:System.ServiceModel.WSHttpBinding> et <xref:System.ServiceModel.NetTcpBinding>, illustre comment définir les modes de sécurité à l'aide d'un programme ou dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="e31a1-108">This topic sets the mode with the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> classes and demonstrates how to set the mode both programmatically and through configuration.</span></span>

<span data-ttu-id="e31a1-109">Pour plus d’informations, consultez sécurité WCF, voir [vue d’ensemble](./feature-details/security-overview.md)de la sécurité, [sécurisation des services](securing-services.md)et [sécurisation des services et des clients](./feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="e31a1-109">For more information, see WCF security, see [Security Overview](./feature-details/security-overview.md), [Securing Services](securing-services.md), and [Securing Services and Clients](./feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="e31a1-110">Pour plus d’informations sur le mode de transport et le message, consultez [sécurité du transport](./feature-details/transport-security.md) et [sécurité des messages](./feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="e31a1-110">For more information about transport mode and message, see [Transport Security](./feature-details/transport-security.md) and [Message Security](./feature-details/message-security-in-wcf.md).</span></span>

## <a name="to-set-the-security-mode-in-code"></a><span data-ttu-id="e31a1-111">Pour définir le mode de sécurité dans le code</span><span class="sxs-lookup"><span data-stu-id="e31a1-111">To set the security mode in code</span></span>

1. <span data-ttu-id="e31a1-112">Créez une instance de la classe de liaison en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="e31a1-112">Create an instance of the binding class that you are using.</span></span> <span data-ttu-id="e31a1-113">Pour obtenir la liste des liaisons prédéfinies, consultez [liaisons fournies par le système](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="e31a1-113">For a list of predefined bindings, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="e31a1-114">Cet exemple de code crée une instance de la classe <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="e31a1-114">This example creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

2. <span data-ttu-id="e31a1-115">Définissez la propriété `Mode` de l'objet retourné par la propriété `Security`.</span><span class="sxs-lookup"><span data-stu-id="e31a1-115">Set the `Mode` property of the object returned by the `Security` property.</span></span>

     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]

     <span data-ttu-id="e31a1-116">Vous pouvez également affecter la valeur message au mode, comme illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="e31a1-116">Alternatively, set the mode to message, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]

     <span data-ttu-id="e31a1-117">Vous pouvez aussi affecter la valeur transport avec informations d'identification de message au mode, comme illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="e31a1-117">Or set the mode to transport with message credentials, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]

3. <span data-ttu-id="e31a1-118">Vous pouvez enfin définir le mode dans le constructeur de la liaison, comme illustré dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="e31a1-118">You can also set the mode in the constructor of the binding, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]

## <a name="setting-the-clientcredentialtype-property"></a><span data-ttu-id="e31a1-119">Définition de la propriété ClientCredentialType</span><span class="sxs-lookup"><span data-stu-id="e31a1-119">Setting the ClientCredentialType Property</span></span>

<span data-ttu-id="e31a1-120">La définition de la propriété `ClientCredentialType` dépend de la valeur affectée au mode de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e31a1-120">Setting the mode to one of the three values determines how you set the `ClientCredentialType` property.</span></span> <span data-ttu-id="e31a1-121">Par exemple, si vous utilisez la classe <xref:System.ServiceModel.WSHttpBinding> et affectez au mode la valeur `Transport` vous devez affecter à la propriété <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> de la classe <xref:System.ServiceModel.HttpTransportSecurity> une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="e31a1-121">For example, using the <xref:System.ServiceModel.WSHttpBinding> class, setting the mode to `Transport` means you must set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property of the <xref:System.ServiceModel.HttpTransportSecurity> class to an appropriate value.</span></span>

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a><span data-ttu-id="e31a1-122">Pour définir la propriété ClientCredentialType pour le mode de sécurité de niveau transport</span><span class="sxs-lookup"><span data-stu-id="e31a1-122">To set the ClientCredentialType property for Transport mode</span></span>

1. <span data-ttu-id="e31a1-123">Créez une instance de la liaison.</span><span class="sxs-lookup"><span data-stu-id="e31a1-123">Create an instance of the binding.</span></span>

2. <span data-ttu-id="e31a1-124">Attribuez à la propriété `Mode` la valeur `Transport`.</span><span class="sxs-lookup"><span data-stu-id="e31a1-124">Set the `Mode` property to `Transport`.</span></span>

3. <span data-ttu-id="e31a1-125">Affectez à la propriété `ClientCredential` une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="e31a1-125">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="e31a1-126">L'exemple de code suivant affecte à la propriété la valeur `Windows`.</span><span class="sxs-lookup"><span data-stu-id="e31a1-126">The following code sets the property to `Windows`.</span></span>

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a><span data-ttu-id="e31a1-127">Pour définir la propriété ClientCredentialType pour le mode de sécurité de niveau message</span><span class="sxs-lookup"><span data-stu-id="e31a1-127">To set the ClientCredentialType property for Message mode</span></span>

1. <span data-ttu-id="e31a1-128">Créez une instance de la liaison.</span><span class="sxs-lookup"><span data-stu-id="e31a1-128">Create an instance of the binding.</span></span>

2. <span data-ttu-id="e31a1-129">Attribuez à la propriété `Mode` la valeur `Message`.</span><span class="sxs-lookup"><span data-stu-id="e31a1-129">Set the `Mode` property to `Message`.</span></span>

3. <span data-ttu-id="e31a1-130">Affectez à la propriété `ClientCredential` une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="e31a1-130">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="e31a1-131">L'exemple de code suivant affecte à la propriété la valeur `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="e31a1-131">The following code sets the property to `Certificate`.</span></span>

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a><span data-ttu-id="e31a1-132">Pour définir le mode et la propriété ClientCredentialType dans la configuration</span><span class="sxs-lookup"><span data-stu-id="e31a1-132">To set the Mode and ClientCredentialType property in configuration</span></span>

1. <span data-ttu-id="e31a1-133">Ajoutez un élément de liaison approprié à l' [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) élément du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e31a1-133">Add an appropriate binding element to the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="e31a1-134">L’exemple suivant ajoute un [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) élément.</span><span class="sxs-lookup"><span data-stu-id="e31a1-134">The following example adds a [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

2. <span data-ttu-id="e31a1-135">Ajoutez un `<binding>` élément et affectez `name` à son attribut une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="e31a1-135">Add a `<binding>` element and set its `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="e31a1-136">Ajoutez un élément `<security>`, puis affectez à l'attribut `mode` les valeurs `Message`, `Transport`ou `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="e31a1-136">Add a `<security>` element and set the `mode` attribute to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

4. <span data-ttu-id="e31a1-137">Si le mode a la valeur `Transport`, ajoutez un élément `<transport>` , puis affectez à l'attribut `clientCredential` une valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="e31a1-137">If the mode is set to `Transport`, add a `<transport>` element and set the `clientCredential` attribute to an appropriate value.</span></span>

     <span data-ttu-id="e31a1-138">L'exemple suivant affecte au mode la valeur `Transport"`, puis affecte à l'attribut `clientCredentialType` de l'élément `<transport>` la valeur `Windows"`.</span><span class="sxs-lookup"><span data-stu-id="e31a1-138">The following example sets the mode to "`Transport"`, and then sets the `clientCredentialType` attribute of the `<transport>` element to "`Windows"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="e31a1-139">Vous pouvez également affecter au `security mode` la valeur `Message"`, suivie d'un élément `<"message">`.</span><span class="sxs-lookup"><span data-stu-id="e31a1-139">Alternatively, set the `security mode` to "`Message"`, followed by a `<"message">` element.</span></span> <span data-ttu-id="e31a1-140">Cet exemple affecte au `clientCredentialType` la valeur `Certificate"`.</span><span class="sxs-lookup"><span data-stu-id="e31a1-140">This example sets the `clientCredentialType` to "`Certificate"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="e31a1-141">L'utilisation de la valeur <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> forme un cas à part, expliqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="e31a1-141">Using the <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> value is a special case, and is explained below.</span></span>

### <a name="using-transportwithmessagecredential"></a><span data-ttu-id="e31a1-142">Utilisation de TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="e31a1-142">Using TransportWithMessageCredential</span></span>

<span data-ttu-id="e31a1-143">Lorsque vous affectez au mode de sécurité la valeur `TransportWithMessageCredential`, le mécanisme chargé d'offrir la sécurité de niveau transport dépend du transport utilisé.</span><span class="sxs-lookup"><span data-stu-id="e31a1-143">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="e31a1-144">Par exemple, le protocole HTTP utilise la sécurité Secure Sockets Layer (SSL) sur HTTP, c'est-à-dire HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e31a1-144">For example, the HTTP protocol uses Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="e31a1-145">Par conséquent, la définition d'une propriété `ClientCredentialType` pour tout objet de sécurité de transport (tel que <xref:System.ServiceModel.HttpTransportSecurity>) sera sans effet.</span><span class="sxs-lookup"><span data-stu-id="e31a1-145">Therefore, setting the `ClientCredentialType` property of any transport security object (such as <xref:System.ServiceModel.HttpTransportSecurity>) is ignored.</span></span>  <span data-ttu-id="e31a1-146">En d’autres termes, vous pouvez uniquement définir la propriété `ClientCredentialType` de l’objet de sécurité de message (pour la liaison `WSHttpBinding`, il s’agit de l’objet <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>).</span><span class="sxs-lookup"><span data-stu-id="e31a1-146">In other words, you can only set the `ClientCredentialType` of the message security object (for the `WSHttpBinding` binding, the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> object).</span></span>

<span data-ttu-id="e31a1-147">Pour plus d’informations, consultez [Comment : utiliser la sécurité de transport et les informations d’identification de message](./feature-details/how-to-use-transport-security-and-message-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="e31a1-147">For more information, see [How to: Use Transport Security and Message Credentials](./feature-details/how-to-use-transport-security-and-message-credentials.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e31a1-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e31a1-148">See also</span></span>

- [<span data-ttu-id="e31a1-149">Comment : configurer un port avec un certificat SSL</span><span class="sxs-lookup"><span data-stu-id="e31a1-149">How to: Configure a Port with an SSL Certificate</span></span>](./feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="e31a1-150">Comment : utiliser des informations d'identification de sécurité de transport et de message</span><span class="sxs-lookup"><span data-stu-id="e31a1-150">How to: Use Transport Security and Message Credentials</span></span>](./feature-details/how-to-use-transport-security-and-message-credentials.md)
- [<span data-ttu-id="e31a1-151">Sécurité de transport</span><span class="sxs-lookup"><span data-stu-id="e31a1-151">Transport Security</span></span>](./feature-details/transport-security.md)
- [<span data-ttu-id="e31a1-152">Sécurité des messages</span><span class="sxs-lookup"><span data-stu-id="e31a1-152">Message Security</span></span>](./feature-details/message-security-in-wcf.md)
- [<span data-ttu-id="e31a1-153">Présentation de la sécurité</span><span class="sxs-lookup"><span data-stu-id="e31a1-153">Security Overview</span></span>](./feature-details/security-overview.md)
- [<span data-ttu-id="e31a1-154">Liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="e31a1-154">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
