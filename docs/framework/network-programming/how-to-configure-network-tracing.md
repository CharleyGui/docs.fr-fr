---
title: Guide pratique pour configurer le suivi réseau
ms.date: 03/30/2017
helpviewer_keywords:
- formatting [.NET Framework], network tracing
- network tracing, configuring
- level attribute
- app.config files, network tracing
- configuration files [.NET Framework], network tracing
- protocol-level trace output
- application configuration files, network tracing
- sockets, trace output
ms.assetid: 5ef9fe4b-8d3d-490e-9259-1d014b2181af
ms.openlocfilehash: 06132509860b16d1e22cfdf7e3226c968d16b7cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73040642"
---
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="640fd-102">Comment configurer le traçage du réseau</span><span class="sxs-lookup"><span data-stu-id="640fd-102">How to: Configure network tracing</span></span>

<span data-ttu-id="640fd-103">Le fichier de configuration de l'application ou de l'ordinateur contient les paramètres qui déterminent le format et le contenu des traces réseau.</span><span class="sxs-lookup"><span data-stu-id="640fd-103">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="640fd-104">Avant d'effectuer cette procédure, assurez-vous que le traçage est activé.</span><span class="sxs-lookup"><span data-stu-id="640fd-104">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="640fd-105">Pour plus d’informations, voir [Suivi du réseau Enable](enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="640fd-105">For more information, see [Enable network tracing](enabling-network-tracing.md).</span></span>

<span data-ttu-id="640fd-106">Le fichier de configuration de l’ordinateur, *machine.config*, est stocké dans le dossier *%windir%-Microsoft.NET-Framework.*</span><span class="sxs-lookup"><span data-stu-id="640fd-106">The computer configuration file, *machine.config*, is stored in the *%windir%\Microsoft.NET\Framework* folder.</span></span> <span data-ttu-id="640fd-107">Il existe un fichier *machine.config* séparé dans les dossiers sous *%windir%-Microsoft.NET-Framework* pour chaque version du cadre .NET installé sur l’ordinateur, par exemple:</span><span class="sxs-lookup"><span data-stu-id="640fd-107">There is a separate *machine.config* file in the folders under *%windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer, for example:</span></span>

- <span data-ttu-id="640fd-108">*C : 'WINDOWS’Microsoft.NET’Framework’v2.0.50727-Config-machine.config*</span><span class="sxs-lookup"><span data-stu-id="640fd-108">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span></span>
- <span data-ttu-id="640fd-109">*C : 'WINDOWS’Microsoft.NET’Framework64'v4.0.30319-Config-machine.config*</span><span class="sxs-lookup"><span data-stu-id="640fd-109">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span></span>

<span data-ttu-id="640fd-110">Ces paramètres peuvent également être effectués dans le fichier de configuration de l'application, qui est prioritaire sur le fichier de configuration de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="640fd-110">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>

## <a name="configure-network-tracing"></a><span data-ttu-id="640fd-111">Configurer le traçage du réseau</span><span class="sxs-lookup"><span data-stu-id="640fd-111">Configure network tracing</span></span>

<span data-ttu-id="640fd-112">Pour configurer le traçage du réseau, ajoutez les lignes suivantes au fichier de configuration approprié.</span><span class="sxs-lookup"><span data-stu-id="640fd-112">To configure network tracing, add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="640fd-113">Les valeurs et les options de ces paramètres sont décrites dans les tableaux ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="640fd-113">The values and options for these settings are described in the tables below.</span></span>

```xml
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Net" tracemode="includehex" maxdatasize="1024">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Cache">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Http">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.Sockets">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
      <source name="System.Net.WebSockets">
        <listeners>
          <add name="System.Net"/>
        </listeners>
      </source>
   </sources>
    <switches>
      <add name="System.Net" value="Verbose"/>
      <add name="System.Net.Cache" value="Verbose"/>
      <add name="System.Net.Http" value="Verbose"/>
      <add name="System.Net.Sockets" value="Verbose"/>
      <add name="System.Net.WebSockets" value="Verbose"/>
    </switches>
    <sharedListeners>
      <add name="System.Net"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="network.log"
        traceOutputOptions="ProcessId, DateTime"
      />
    </sharedListeners>
    <trace autoflush="true"/>
  </system.diagnostics>
</configuration>
```

### <a name="trace-output-from-methods"></a><span data-ttu-id="640fd-114">Sortie de trace des méthodes</span><span class="sxs-lookup"><span data-stu-id="640fd-114">Trace output from methods</span></span>

<span data-ttu-id="640fd-115">Lorsque vous ajoutez un nom au bloc `<switches>`, la sortie de trace inclut les informations de certaines méthodes associées au nom.</span><span class="sxs-lookup"><span data-stu-id="640fd-115">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="640fd-116">Le tableau suivant décrit la sortie :</span><span class="sxs-lookup"><span data-stu-id="640fd-116">The following table describes the output:</span></span>

|<span data-ttu-id="640fd-117">Nom</span><span class="sxs-lookup"><span data-stu-id="640fd-117">Name</span></span>|<span data-ttu-id="640fd-118">Sortie de</span><span class="sxs-lookup"><span data-stu-id="640fd-118">Output from</span></span>|
|----------|-----------------|
|`System.Net.Sockets`|<span data-ttu-id="640fd-119">Quelques méthodes publiques <xref:System.Net.Sockets.Socket> <xref:System.Net.Sockets.TcpListener>de <xref:System.Net.Sockets.TcpClient>la <xref:System.Net.Dns> , , et les classes.</span><span class="sxs-lookup"><span data-stu-id="640fd-119">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes.</span></span>|
|`System.Net`|<span data-ttu-id="640fd-120">Quelques méthodes publiques <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebResponse>de <xref:System.Net.FtpWebRequest>la <xref:System.Net.FtpWebResponse> , , et les classes, et SSL débobli des informations (certificats invalides, liste d’émetteurs manquants, et erreurs de certificat client).</span><span class="sxs-lookup"><span data-stu-id="640fd-120">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors).</span></span>|
|`System.Net.HttpListener`|<span data-ttu-id="640fd-121">Certaines méthodes publiques des classes <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest> et <xref:System.Net.HttpListenerResponse>.</span><span class="sxs-lookup"><span data-stu-id="640fd-121">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|
|`System.Net.Cache`|<span data-ttu-id="640fd-122">Certaines méthodes privées et internes dans `System.Net.Cache`.</span><span class="sxs-lookup"><span data-stu-id="640fd-122">Some private and internal methods in `System.Net.Cache`.</span></span>|
|`System.Net.Http`|<span data-ttu-id="640fd-123">Certaines méthodes publiques des classes <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler> et <xref:System.Net.Http.WebRequestHandler>.</span><span class="sxs-lookup"><span data-stu-id="640fd-123">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="640fd-124">Certaines méthodes publiques des classes <xref:System.Net.WebSockets.ClientWebSocket> et <xref:System.Net.WebSockets.WebSocket>.</span><span class="sxs-lookup"><span data-stu-id="640fd-124">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|

### <a name="trace-output-attributes"></a><span data-ttu-id="640fd-125">Attributs de sortie de trace</span><span class="sxs-lookup"><span data-stu-id="640fd-125">Trace output attributes</span></span>

<span data-ttu-id="640fd-126">Les attributs énumérés dans le tableau suivant configurent la sortie de trace :</span><span class="sxs-lookup"><span data-stu-id="640fd-126">The attributes listed in the following table configure trace output:</span></span>

|<span data-ttu-id="640fd-127">Nom de l’attribut</span><span class="sxs-lookup"><span data-stu-id="640fd-127">Attribute name</span></span>|<span data-ttu-id="640fd-128">Valeur d'attribut</span><span class="sxs-lookup"><span data-stu-id="640fd-128">Attribute value</span></span>|
|--------------------|---------------------|
|`value`|<span data-ttu-id="640fd-129">Attribut <xref:System.String> requis.</span><span class="sxs-lookup"><span data-stu-id="640fd-129">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="640fd-130">Définit les commentaires de la sortie.</span><span class="sxs-lookup"><span data-stu-id="640fd-130">Sets the verbosity of the output.</span></span> <span data-ttu-id="640fd-131">Les valeurs légitimes sont `Critical`, `Error`, `Verbose`, `Warning` et `Information`.</span><span class="sxs-lookup"><span data-stu-id="640fd-131">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /><span data-ttu-id="640fd-132">Cet attribut doit être défini sur l’élément **add** de l’élément **commutateurs.**</span><span class="sxs-lookup"><span data-stu-id="640fd-132">This attribute must be set on the **add** element of the **switches** element.</span></span> <span data-ttu-id="640fd-133">Une exception est projetée si cet attribut est défini sur l’élément **source.**</span><span class="sxs-lookup"><span data-stu-id="640fd-133">An exception is thrown if this attribute is set on the **source** element.</span></span><br/><br/><span data-ttu-id="640fd-134">Exemple : `<add name="System.Net" value="Verbose"/>`</span><span class="sxs-lookup"><span data-stu-id="640fd-134">Example: `<add name="System.Net" value="Verbose"/>`</span></span>|
|`maxdatasize`|<span data-ttu-id="640fd-135">Attribut <xref:System.Int32> facultatif.</span><span class="sxs-lookup"><span data-stu-id="640fd-135">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="640fd-136">Définit le nombre maximal d'octets de données réseau incluses dans chaque trace de ligne.</span><span class="sxs-lookup"><span data-stu-id="640fd-136">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="640fd-137">La valeur par défaut est 1024.</span><span class="sxs-lookup"><span data-stu-id="640fd-137">The default value is 1024.</span></span><br /><br /><span data-ttu-id="640fd-138">Cet attribut doit être défini sur l’élément **source.**</span><span class="sxs-lookup"><span data-stu-id="640fd-138">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="640fd-139">Une exception est projetée si cet attribut est défini sur un élément sous **l’élément des commutateurs.**</span><span class="sxs-lookup"><span data-stu-id="640fd-139">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="640fd-140">Exemple : `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="640fd-140">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|
|`tracemode`|<span data-ttu-id="640fd-141">Attribut <xref:System.String> facultatif.</span><span class="sxs-lookup"><span data-stu-id="640fd-141">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="640fd-142">Définissez la valeur `includehex` pour afficher les traces de protocole au format hexadécimal et texte.</span><span class="sxs-lookup"><span data-stu-id="640fd-142">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="640fd-143">Définissez la valeur `protocolonly` pour afficher uniquement du texte.</span><span class="sxs-lookup"><span data-stu-id="640fd-143">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="640fd-144">La valeur par défaut est `includehex`.</span><span class="sxs-lookup"><span data-stu-id="640fd-144">The default value is `includehex`.</span></span><br /><br /><span data-ttu-id="640fd-145">Cet attribut doit être défini sur l’élément **source.**</span><span class="sxs-lookup"><span data-stu-id="640fd-145">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="640fd-146">Une exception est projetée si cet attribut est défini sur un élément sous **l’élément des commutateurs.**</span><span class="sxs-lookup"><span data-stu-id="640fd-146">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="640fd-147">Exemple : `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="640fd-147">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|

## <a name="see-also"></a><span data-ttu-id="640fd-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="640fd-148">See also</span></span>

- [<span data-ttu-id="640fd-149">Interprétation du suivi réseau</span><span class="sxs-lookup"><span data-stu-id="640fd-149">Interpreting Network Tracing</span></span>](interpreting-network-tracing.md)
- [<span data-ttu-id="640fd-150">Traçage réseau dans .NET Framework</span><span class="sxs-lookup"><span data-stu-id="640fd-150">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
- [<span data-ttu-id="640fd-151">Activation du traçage réseau</span><span class="sxs-lookup"><span data-stu-id="640fd-151">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="640fd-152">Traçage et instrumentation d'applications</span><span class="sxs-lookup"><span data-stu-id="640fd-152">Tracing and Instrumenting Applications</span></span>](../debug-trace-profile/tracing-and-instrumenting-applications.md)
