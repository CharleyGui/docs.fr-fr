---
title: <network>, élément (paramètres réseau)
description: L' <network> élément paramètres réseau configure les options réseau pour les options de serveur SMTP externe dans le .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: cd142febc0b3aacf1be7978178a6a05d9b9aebbf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190278"
---
# <a name="network-element-network-settings"></a><span data-ttu-id="2ecec-103">\<network>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="2ecec-103">\<network> Element (Network Settings)</span></span>

<span data-ttu-id="2ecec-104">Configure les options réseau pour un serveur SMTP (simple mail transport Protocol) externe.</span><span class="sxs-lookup"><span data-stu-id="2ecec-104">Configures the network options for an external Simple Mail Transport Protocol (SMTP) server.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<network>**

## <a name="syntax"></a><span data-ttu-id="2ecec-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ecec-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ecec-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2ecec-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2ecec-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2ecec-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ecec-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="2ecec-108">Attributes</span></span>  
  
|<span data-ttu-id="2ecec-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="2ecec-109">Attribute</span></span>|<span data-ttu-id="2ecec-110">Description</span><span class="sxs-lookup"><span data-stu-id="2ecec-110">Description</span></span>|  
|---------------|-----------------|  
|`clientDomain`|<span data-ttu-id="2ecec-111">Spécifie le nom de domaine client à utiliser dans la demande de protocole SMTP initiale pour se connecter au serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ecec-111">Specifies the client domain name to use in the initial SMTP protocol request to connect to the SMTP mail server.</span></span> <span data-ttu-id="2ecec-112">La valeur par défaut est le nom localhost de l’ordinateur local qui envoie la demande.</span><span class="sxs-lookup"><span data-stu-id="2ecec-112">The default value is the localhost name of the local computer sending the request.</span></span>|  
|`defaultCredentials`|<span data-ttu-id="2ecec-113">Spécifie si les informations d’identification de l’utilisateur par défaut doivent être utilisées pour accéder au serveur de messagerie SMTP pour les transactions SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ecec-113">Specifies whether the default user credentials should be used to access the SMTP mail server for SMTP transactions.</span></span> <span data-ttu-id="2ecec-114">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="2ecec-114">The default value is `false`.</span></span>|  
|`enableSsl`|<span data-ttu-id="2ecec-115">Spécifie si le protocole SSL est utilisé pour accéder à un serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ecec-115">Specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="2ecec-116">La valeur par défaut est `false`.</span><span class="sxs-lookup"><span data-stu-id="2ecec-116">The default value is `false`.</span></span>|  
|`host`|<span data-ttu-id="2ecec-117">Spécifie le nom d’hôte du serveur de messagerie SMTP à utiliser pour les transactions SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ecec-117">Specifies the hostname of the SMTP mail server to use for SMTP transactions.</span></span> <span data-ttu-id="2ecec-118">Cet attribut n’a aucune valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2ecec-118">This attribute has no default value.</span></span>|  
|`password`|<span data-ttu-id="2ecec-119">Spécifie le mot de passe à utiliser pour l’authentification auprès du serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ecec-119">Specifies the password to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="2ecec-120">Cet attribut n’a aucune valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2ecec-120">This attribute has no default value.</span></span>|  
|`port`|<span data-ttu-id="2ecec-121">Spécifie le numéro de port à utiliser pour se connecter au serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ecec-121">Specifies the port number to use to connect to the SMTP mail server.</span></span> <span data-ttu-id="2ecec-122">La valeur par défaut est 25.</span><span class="sxs-lookup"><span data-stu-id="2ecec-122">The default value is 25.</span></span>|  
|`targetName`|<span data-ttu-id="2ecec-123">Spécifie le nom du fournisseur de services (SPN) à utiliser pour l’authentification lors de l’utilisation de la protection étendue pour les transactions SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ecec-123">Specifies the Service Provider Name (SPN) to use for authentication when using extended protection for SMTP transactions.</span></span> <span data-ttu-id="2ecec-124">Cet attribut n’a aucune valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2ecec-124">This attribute has no default value.</span></span>|  
|`userName`|<span data-ttu-id="2ecec-125">Spécifie le nom d’utilisateur à utiliser pour l’authentification auprès du serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ecec-125">Specifies the user name to use for authentication to the SMTP mail server.</span></span> <span data-ttu-id="2ecec-126">Cet attribut n’a aucune valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2ecec-126">This attribute has no default value.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ecec-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2ecec-127">Child Elements</span></span>  

 <span data-ttu-id="2ecec-128">Aucun.</span><span class="sxs-lookup"><span data-stu-id="2ecec-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ecec-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2ecec-129">Parent Elements</span></span>  
  
|<span data-ttu-id="2ecec-130">Élément</span><span class="sxs-lookup"><span data-stu-id="2ecec-130">Element</span></span>|<span data-ttu-id="2ecec-131">Description</span><span class="sxs-lookup"><span data-stu-id="2ecec-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ecec-132">\<smtp> , Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="2ecec-132">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="2ecec-133">Configure les options d’envoi de courrier SMTP (simple mail transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="2ecec-133">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ecec-134">Notes</span><span class="sxs-lookup"><span data-stu-id="2ecec-134">Remarks</span></span>  

 <span data-ttu-id="2ecec-135">Certains serveurs SMTP nécessitent que vous vous authentifiez auprès du serveur avant de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="2ecec-135">Some SMTP servers require that you authenticate yourself to the server before use.</span></span> <span data-ttu-id="2ecec-136">Si vous souhaitez vous authentifier à l’aide des informations d’identification réseau par défaut sur votre ordinateur hôte, affectez la valeur `defaultCredentials` à l’attribut `true` .</span><span class="sxs-lookup"><span data-stu-id="2ecec-136">If you want to authenticate yourself using the default network credentials on your host, set the `defaultCredentials` attribute to `true`.</span></span> <span data-ttu-id="2ecec-137">La <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> propriété peut être utilisée pour récupérer la valeur actuelle de l' `defaultCredentials` attribut à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="2ecec-137">The <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType> property can be used to get the current value of the `defaultCredentials` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="2ecec-138">Vous pouvez également utiliser l’authentification de base (un nom d’utilisateur et un mot de passe) pour vous authentifier auprès du serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ecec-138">You can also use basic authentication (a user name and password) to authenticate yourself to the SMTP server.</span></span> <span data-ttu-id="2ecec-139">Pour utiliser cette option, vous devez spécifier un nom d’utilisateur et un mot de passe valides pour le serveur SMTP spécifié.</span><span class="sxs-lookup"><span data-stu-id="2ecec-139">To use this option, you must specify a valid user name and password for the specified SMTP server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2ecec-140">L’authentification de base envoie les `userName` `password` valeurs et au serveur non chiffré.</span><span class="sxs-lookup"><span data-stu-id="2ecec-140">Basic authentication sends the `userName` and `password` values to the server unencrypted.</span></span> <span data-ttu-id="2ecec-141">Toute personne surveillant le trafic réseau peut afficher vos informations d’identification et les utiliser pour se connecter au serveur.</span><span class="sxs-lookup"><span data-stu-id="2ecec-141">Anyone monitoring network traffic can view your credentials and use them to connect to the server.</span></span> <span data-ttu-id="2ecec-142">Vous devez envisager d’utiliser un mécanisme d’authentification plus sécurisé, tel que Kerberos ou NT LAN Manager (NTLM). Si `defaultCredentials` est `true` , Kerberos ou NTLM sera utilisé si le serveur prend en charge ces protocoles.</span><span class="sxs-lookup"><span data-stu-id="2ecec-142">You should consider using a more secure authentication mechanism, such as Kerberos or NT LAN Manager (NTLM.) If `defaultCredentials` is `true`, Kerberos or NTLM will be used if the server supports these protocols.</span></span>  
  
 <span data-ttu-id="2ecec-143">Les options authentification de base et informations d’identification réseau par défaut s’excluent mutuellement ; Si vous affectez `defaultCredentials` à `true` la valeur et spécifiez un nom d’utilisateur et un mot de passe, les informations d’identification réseau par défaut sont utilisées et les données d’authentification de base sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="2ecec-143">The basic authentication and default network credentials options are mutually exclusive; if you set `defaultCredentials` to `true` and specify a user name and password, the default network credential is used, and the basic authentication data is ignored.</span></span>  
  
 <span data-ttu-id="2ecec-144">Pour l’authentification de base si vous spécifiez un `userName` , vous devez également spécifier un `password` pour vous authentifier auprès du serveur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="2ecec-144">For basic authentication if you specify a `userName`, you should also specify a `password` to authentication yourself to the mail server.</span></span>  
  
 <span data-ttu-id="2ecec-145">La <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> propriété peut être utilisée pour récupérer la valeur actuelle de l' `userName` attribut à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="2ecec-145">The <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType> property can be used to get the current value of the `userName` attribute from applicable configuration files.</span></span> <span data-ttu-id="2ecec-146">La <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> propriété peut être utilisée pour récupérer la valeur actuelle de l' `password` attribut à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="2ecec-146">The <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType> property can be used to get the current value of the `password` attribute from applicable configuration files.</span></span> <span data-ttu-id="2ecec-147">Aucun `password` attribut n’est normalement entré dans les fichiers de configuration pour des raisons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="2ecec-147">A `password` attribute would not normally be entered in configuration files for security reasons.</span></span>  
  
 <span data-ttu-id="2ecec-148">L' `clientDomain` attribut modifie le nom de domaine client utilisé dans la demande de protocole SMTP initiale pour un serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ecec-148">The `clientDomain` attribute changes the client domain name used in the initial SMTP protocol request to an SMTP server.</span></span> <span data-ttu-id="2ecec-149">L' `clientDomain` attribut peut être défini sur le nom de domaine complet de l’ordinateur local, plutôt que sur le nom localhost qui est utilisé par défaut.</span><span class="sxs-lookup"><span data-stu-id="2ecec-149">The `clientDomain` attribute can be set to the fully-qualified domain name of the local machine, rather than the localhost name that is used by default.</span></span> <span data-ttu-id="2ecec-150">Cela offre une meilleure conformité avec les normes de protocole SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ecec-150">This provides greater compliance with the SMTP protocol standards.</span></span> <span data-ttu-id="2ecec-151">La valeur par défaut est le nom localhost de l’ordinateur local qui envoie la demande.</span><span class="sxs-lookup"><span data-stu-id="2ecec-151">The default value is the localhost name of the local computer sending the request.</span></span> <span data-ttu-id="2ecec-152">La <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> propriété peut être utilisée pour récupérer la valeur actuelle de l' `clientDomain` attribut à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="2ecec-152">The <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType> property can be used to get the current value of the `clientDomain` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="2ecec-153">L' `targetName` attribut est utilisé pour l’authentification lors de l’utilisation de la protection étendue.</span><span class="sxs-lookup"><span data-stu-id="2ecec-153">The `targetName` attribute is used for authentication when using extended protection.</span></span> <span data-ttu-id="2ecec-154">La valeur par défaut se présente sous la forme « SMTPSVC/ \<host> » \<host> , où est le nom d’hôte du serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ecec-154">The default value is of the form "SMTPSVC/\<host>" where \<host> is the hostname of the SMTP mail server.</span></span> <span data-ttu-id="2ecec-155">La <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> propriété peut être utilisée pour récupérer la valeur actuelle de l' `targetName` attribut à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="2ecec-155">The <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType> property can be used to get the current value of the `targetName` attribute from applicable configuration files.</span></span>  
  
 <span data-ttu-id="2ecec-156">L' `enableSsl` attribut spécifie si le protocole SSL est utilisé pour accéder à un serveur de messagerie SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ecec-156">The `enableSsl` attribute specifies whether SSL is used to access an SMTP mail server.</span></span> <span data-ttu-id="2ecec-157">La <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> classe prend en charge uniquement l’extension de service SMTP pour SMTP sécurisé sur Transport Layer Security, comme défini dans la norme RFC 3207.</span><span class="sxs-lookup"><span data-stu-id="2ecec-157">The <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType> class only supports the SMTP Service Extension for Secure SMTP over Transport Layer Security as defined in RFC 3207.</span></span> <span data-ttu-id="2ecec-158">Dans ce mode, la session SMTP commence sur un canal non chiffré, puis une commande STARTTLS est émise par le client vers le serveur pour basculer vers une communication sécurisée à l’aide de SSL.</span><span class="sxs-lookup"><span data-stu-id="2ecec-158">In this mode, the SMTP session begins on an unencrypted channel, then a STARTTLS command is issued by the client to the server to switch to secure communication using SSL.</span></span> <span data-ttu-id="2ecec-159">Pour plus d’informations, consultez RFC 3207 publié par l’IETF (Internet Engineering Task Force).</span><span class="sxs-lookup"><span data-stu-id="2ecec-159">See RFC 3207 published by the Internet Engineering Task Force (IETF) for more information.</span></span>  
  
 <span data-ttu-id="2ecec-160">Une autre méthode de connexion est l’emplacement où une session SSL est établie au préalable avant l’envoi des commandes de protocole.</span><span class="sxs-lookup"><span data-stu-id="2ecec-160">An alternate connection method is where an SSL session is established up front before any protocol commands are sent.</span></span> <span data-ttu-id="2ecec-161">Cette méthode de connexion est parfois appelée SMTPs et utilise par défaut le port 465.</span><span class="sxs-lookup"><span data-stu-id="2ecec-161">This connection method is sometimes called SMTPS and by default uses port 465.</span></span> <span data-ttu-id="2ecec-162">Cette autre méthode de connexion utilisant SSL n’est pas prise en charge actuellement.</span><span class="sxs-lookup"><span data-stu-id="2ecec-162">This alternate connection method using SSL is not currently supported.</span></span>  
  
 <span data-ttu-id="2ecec-163">La <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> propriété peut être utilisée pour récupérer la valeur actuelle de l' `enableSsl` attribut à partir des fichiers de configuration applicables.</span><span class="sxs-lookup"><span data-stu-id="2ecec-163">The <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType> property can be used to get the current value of the `enableSsl` attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ecec-164">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ecec-164">Example</span></span>  

 <span data-ttu-id="2ecec-165">L’exemple suivant spécifie les paramètres SMTP appropriés pour envoyer des messages électroniques à l’aide des informations d’identification réseau par défaut.</span><span class="sxs-lookup"><span data-stu-id="2ecec-165">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2ecec-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ecec-166">See also</span></span>

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [<span data-ttu-id="2ecec-167">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="2ecec-167">Network Settings Schema</span></span>](index.md)
