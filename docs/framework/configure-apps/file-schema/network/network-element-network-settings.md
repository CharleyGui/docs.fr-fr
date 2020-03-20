---
title: <network>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: f7cfcc3b9d5a717c23175cd15aa48ae97c828e57
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154814"
---
# <a name="network-element-network-settings"></a><span data-ttu-id="9b31d-102">\<> element réseau (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="9b31d-102">\<network> Element (Network Settings)</span></span>
<span data-ttu-id="9b31d-103">Configure les options réseau pour un serveur externe Simple Mail Transport Protocol (SMTP).</span><span class="sxs-lookup"><span data-stu-id="9b31d-103">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  

<span data-ttu-id="9b31d-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9b31d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9b31d-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="9b31d-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="9b31d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="9b31d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="9b31d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>smtp**](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="9b31d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>\
<span data-ttu-id="9b31d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>réseau**</span><span class="sxs-lookup"><span data-stu-id="9b31d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<network>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9b31d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b31d-109">Syntax</span></span>  
  
```xml  
<network  
  clientDomain="string"
  defaultCredentials="true|false"  
  enableSsl="true|false"  
  host="string"
  password="string"  
  port="integer"
  targetName="string"  
  userName="string"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b31d-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9b31d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9b31d-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9b31d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b31d-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="9b31d-112">Attributes</span></span>  
  
|<span data-ttu-id="9b31d-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="9b31d-113">Attribute</span></span>|<span data-ttu-id="9b31d-114">Description</span><span class="sxs-lookup"><span data-stu-id="9b31d-114">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="9b31d-115">Spécifie le nom de domaine client à utiliser dans la demande initiale de protocole SMTP pour se connecter au serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="9b31d-115">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="9b31d-116">La valeur par défaut est le nom localhost de l’ordinateur local d’envoi de la demande.</span><span class="sxs-lookup"><span data-stu-id="9b31d-116">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="9b31d-117">Précise si les informations d’identification des utilisateurs par défaut doivent être utilisées pour accéder au serveur de messagerie SMTP pour les transactions SMTP.</span><span class="sxs-lookup"><span data-stu-id="9b31d-117">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="9b31d-118">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="9b31d-118">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="9b31d-119">Précise si SSL est utilisé pour accéder à un serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="9b31d-119">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="9b31d-120">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="9b31d-120">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="9b31d-121">Spécifie le nom d’hôte du serveur de messagerie SMTP à utiliser pour les transactions SMTP.</span><span class="sxs-lookup"><span data-stu-id="9b31d-121">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="9b31d-122">Cet attribut n’a aucune valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="9b31d-122">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="9b31d-123">Spécifie le mot de passe à utiliser pour l’authentification du serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="9b31d-123">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="9b31d-124">Cet attribut n’a aucune valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="9b31d-124">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="9b31d-125">Spécifie le numéro de port à utiliser pour se connecter au serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="9b31d-125">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="9b31d-126">La valeur par défaut est 25.</span><span class="sxs-lookup"><span data-stu-id="9b31d-126">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="9b31d-127">Spécifie le nom du fournisseur de services (SPN) à utiliser pour l’authentification lors de l’utilisation d’une protection étendue pour les transactions SMTP.</span><span class="sxs-lookup"><span data-stu-id="9b31d-127">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="9b31d-128">Cet attribut n’a aucune valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="9b31d-128">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="9b31d-129">Spécifie le nom d’utilisateur à utiliser pour l’authentification du serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="9b31d-129">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="9b31d-130">Cet attribut n’a aucune valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="9b31d-130">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9b31d-131">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9b31d-131">Child Elements</span></span>  
 <span data-ttu-id="9b31d-132">Aucun.</span><span class="sxs-lookup"><span data-stu-id="9b31d-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9b31d-133">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9b31d-133">Parent Elements</span></span>  
  
|<span data-ttu-id="9b31d-134">Élément</span><span class="sxs-lookup"><span data-stu-id="9b31d-134">Element</span></span>|<span data-ttu-id="9b31d-135">Description</span><span class="sxs-lookup"><span data-stu-id="9b31d-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b31d-136">\<smtp> Element (Paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="9b31d-136">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="9b31d-137">Configure les options d’envoi de courrier simple par protocole de transport de courrier (SMTP).</span><span class="sxs-lookup"><span data-stu-id="9b31d-137">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b31d-138">Notes </span><span class="sxs-lookup"><span data-stu-id="9b31d-138">Remarks</span></span>  
 <span data-ttu-id="9b31d-139">Certains serveurs SMTP exigent que vous vous authentifiiez au serveur avant utilisation.</span><span class="sxs-lookup"><span data-stu-id="9b31d-139">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="9b31d-140">Si vous souhaitez vous authentifier à l’aide `defaultCredentials` des `true`informations d’identification réseau par défaut de votre hôte, définissez l’attribut à .</span><span class="sxs-lookup"><span data-stu-id="9b31d-140">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="9b31d-141">La <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> propriété peut être utilisée pour `defaultCredentials` obtenir la valeur actuelle de l’attribut à partir de fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="9b31d-141">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="9b31d-142">Vous pouvez également utiliser l’authentification de base (nom d’utilisateur et mot de passe) pour vous authentifier au serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="9b31d-142">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="9b31d-143">Pour utiliser cette option, vous devez spécifier un nom d’utilisateur et un mot de passe valides pour le serveur SMTP spécifié.</span><span class="sxs-lookup"><span data-stu-id="9b31d-143">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b31d-144">L’authentification `password` de base envoie le et les `userName` valeurs au serveur non chiffré.</span><span class="sxs-lookup"><span data-stu-id="9b31d-144">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="9b31d-145">Toute personne surveillant le trafic réseau peut afficher vos informations d’identification et les utiliser pour se connecter au serveur.</span><span class="sxs-lookup"><span data-stu-id="9b31d-145">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="9b31d-146">Vous devriez envisager d’utiliser un mécanisme d’authentification plus sécurisé, comme Kerberos ou NT LAN Manager (NTLM.) Si `defaultCredentials` `true`c’est , Kerberos ou NTLM sera utilisé si le serveur prend en charge ces protocoles.</span><span class="sxs-lookup"><span data-stu-id="9b31d-146">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="9b31d-147">Les options d’authentification de base et d’informations d’identification par défaut du réseau s’excluent mutuellement ; si vous `defaultCredentials` `true` définissez et spécifiez un nom d’utilisateur et un mot de passe, l’identifiant réseau par défaut est utilisé, et les données d’authentification de base sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="9b31d-147">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="9b31d-148">Pour l’authentification `userName`de base si `password` vous spécifiez un , vous devez également spécifier un pour vous authentifier au serveur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="9b31d-148">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="9b31d-149">La <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> propriété peut être utilisée pour `userName` obtenir la valeur actuelle de l’attribut à partir de fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="9b31d-149">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="9b31d-150">La <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> propriété peut être utilisée pour `password` obtenir la valeur actuelle de l’attribut à partir de fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="9b31d-150">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="9b31d-151">Un `password` attribut ne serait normalement pas entré dans les fichiers de configuration pour des raisons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="9b31d-151">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="9b31d-152">L’attribut `clientDomain` modifie le nom de domaine du client utilisé dans la demande initiale de protocole SMTP à un serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="9b31d-152">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="9b31d-153">L’attribut `clientDomain` peut être défini au nom de domaine entièrement qualifié de la machine locale, plutôt qu’au nom local d’host qui est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="9b31d-153">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="9b31d-154">Cela permet une plus grande conformité aux normes du protocole SMTP.</span><span class="sxs-lookup"><span data-stu-id="9b31d-154">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="9b31d-155">La valeur par défaut est le nom localhost de l’ordinateur local d’envoi de la demande.</span><span class="sxs-lookup"><span data-stu-id="9b31d-155">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="9b31d-156">La <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> propriété peut être utilisée pour `clientDomain` obtenir la valeur actuelle de l’attribut à partir de fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="9b31d-156">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="9b31d-157">L’attribut `targetName` est utilisé pour l’authentification lors de l’utilisation d’une protection étendue.</span><span class="sxs-lookup"><span data-stu-id="9b31d-157">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="9b31d-158">La valeur par défaut est du formulaire\<"SMTPSVC/ \<host>" où l’hôte> est le nom hôte du serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="9b31d-158">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="9b31d-159">La <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> propriété peut être utilisée pour `targetName` obtenir la valeur actuelle de l’attribut à partir de fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="9b31d-159">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="9b31d-160">L’attribut `enableSsl` précise si SSL est utilisé pour accéder à un serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="9b31d-160">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="9b31d-161">La <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> classe ne prend en charge que l’extension de service SMTP pour secure SMTP sur la sécurité des couches de transport telle que définie dans RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="9b31d-161">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="9b31d-162">Dans ce mode, la session SMTP commence sur un canal non crypté, puis une commande STARTTLS est délivrée par le client au serveur pour passer à la communication sécurisée à l’aide de SSL.</span><span class="sxs-lookup"><span data-stu-id="9b31d-162">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="9b31d-163">Voir RFC 3207 publié par l’Internet Engineering Task Force (IETF) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="9b31d-163">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="9b31d-164">Une autre méthode de connexion est l’endroit où une session SSL est établie à l’avance avant que des commandes de protocole soient envoyées.</span><span class="sxs-lookup"><span data-stu-id="9b31d-164">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="9b31d-165">Cette méthode de connexion est parfois appelée SMTPS et utilise par défaut le port 465.</span><span class="sxs-lookup"><span data-stu-id="9b31d-165">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="9b31d-166">Cette méthode de connexion alternative utilisant SSL n’est pas actuellement prise en charge.</span><span class="sxs-lookup"><span data-stu-id="9b31d-166">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="9b31d-167">La <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> propriété peut être utilisée pour `enableSsl` obtenir la valeur actuelle de l’attribut à partir de fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="9b31d-167">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b31d-168"> Exemple</span><span class="sxs-lookup"><span data-stu-id="9b31d-168">Example</span></span>  
 <span data-ttu-id="9b31d-169">L’exemple suivant spécifie les paramètres SMTP appropriés pour envoyer des e-mails à l’aide des informations d’identification réseau par défaut.</span><span class="sxs-lookup"><span data-stu-id="9b31d-169">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          clientDomain="www.contoso.com"  
          defaultCredentials="true"  
          enableSsl="false"  
          host="mail.contoso.com"  
          port="25"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b31d-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b31d-170">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="9b31d-171">Paramètres réseau Schema</span><span class="sxs-lookup"><span data-stu-id="9b31d-171">Network Settings Schema</span></span>](index.md)
