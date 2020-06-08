---
title: Guide pratique pour configurer le suivi réseau
description: Découvrez comment configurer le traçage réseau dans le fichier de configuration de l’ordinateur ou dans le fichier de configuration de l’application. Un fichier de configuration d’application est prioritaire.
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
ms.openlocfilehash: b089746e9838c591ed5ccc9ac9aaeedb217de9a9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502559"
---
# <a name="how-to-configure-network-tracing"></a><span data-ttu-id="74dcd-104">Procédure : configurer le traçage réseau</span><span class="sxs-lookup"><span data-stu-id="74dcd-104">How to: Configure network tracing</span></span>

<span data-ttu-id="74dcd-105">Le fichier de configuration de l'application ou de l'ordinateur contient les paramètres qui déterminent le format et le contenu des traces réseau.</span><span class="sxs-lookup"><span data-stu-id="74dcd-105">The application or computer configuration file holds the settings that determine the format and content of network traces.</span></span> <span data-ttu-id="74dcd-106">Avant d'effectuer cette procédure, assurez-vous que le traçage est activé.</span><span class="sxs-lookup"><span data-stu-id="74dcd-106">Before performing this procedure, be sure tracing is enabled.</span></span> <span data-ttu-id="74dcd-107">Pour plus d’informations, consultez [activer le traçage réseau](enabling-network-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="74dcd-107">For more information, see [Enable network tracing](enabling-network-tracing.md).</span></span>

<span data-ttu-id="74dcd-108">Le fichier de configuration de l’ordinateur, *machine. config*, est stocké dans le dossier *%windir%\Microsoft.NET\Framework*</span><span class="sxs-lookup"><span data-stu-id="74dcd-108">The computer configuration file, *machine.config*, is stored in the *%windir%\Microsoft.NET\Framework* folder.</span></span> <span data-ttu-id="74dcd-109">Il existe un fichier *machine. config* distinct dans les dossiers sous *%windir%\Microsoft.NET\Framework* pour chaque version du .NET Framework installée sur l’ordinateur, par exemple :</span><span class="sxs-lookup"><span data-stu-id="74dcd-109">There is a separate *machine.config* file in the folders under *%windir%\Microsoft.NET\Framework* for each version of the .NET Framework installed on the computer, for example:</span></span>

- <span data-ttu-id="74dcd-110">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="74dcd-110">*C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\Config\machine.config*</span></span>
- <span data-ttu-id="74dcd-111">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span><span class="sxs-lookup"><span data-stu-id="74dcd-111">*C:\WINDOWS\Microsoft.NET\Framework64\v4.0.30319\Config\machine.config*</span></span>

<span data-ttu-id="74dcd-112">Ces paramètres peuvent également être effectués dans le fichier de configuration de l'application, qui est prioritaire sur le fichier de configuration de votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="74dcd-112">These settings can also be made in the configuration file for the application, which has precedence over the computer configuration file.</span></span>

## <a name="configure-network-tracing"></a><span data-ttu-id="74dcd-113">Configurer le traçage réseau</span><span class="sxs-lookup"><span data-stu-id="74dcd-113">Configure network tracing</span></span>

<span data-ttu-id="74dcd-114">Pour configurer le traçage réseau, ajoutez les lignes suivantes au fichier de configuration approprié.</span><span class="sxs-lookup"><span data-stu-id="74dcd-114">To configure network tracing, add the following lines to the appropriate configuration file.</span></span> <span data-ttu-id="74dcd-115">Les valeurs et les options de ces paramètres sont décrites dans les tableaux ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="74dcd-115">The values and options for these settings are described in the tables below.</span></span>

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

### <a name="trace-output-from-methods"></a><span data-ttu-id="74dcd-116">Sortie de suivi des méthodes</span><span class="sxs-lookup"><span data-stu-id="74dcd-116">Trace output from methods</span></span>

<span data-ttu-id="74dcd-117">Lorsque vous ajoutez un nom au bloc `<switches>`, la sortie de trace inclut les informations de certaines méthodes associées au nom.</span><span class="sxs-lookup"><span data-stu-id="74dcd-117">When you add a name to the `<switches>` block, the trace output includes information from some methods related to the name.</span></span> <span data-ttu-id="74dcd-118">Le tableau suivant décrit la sortie :</span><span class="sxs-lookup"><span data-stu-id="74dcd-118">The following table describes the output:</span></span>

|<span data-ttu-id="74dcd-119">Nom</span><span class="sxs-lookup"><span data-stu-id="74dcd-119">Name</span></span>|<span data-ttu-id="74dcd-120">Sortie de</span><span class="sxs-lookup"><span data-stu-id="74dcd-120">Output from</span></span>|
|----------|-----------------|
|`System.Net.Sockets`|<span data-ttu-id="74dcd-121">Certaines méthodes publiques des <xref:System.Net.Sockets.Socket> classes, <xref:System.Net.Sockets.TcpListener> , <xref:System.Net.Sockets.TcpClient> et <xref:System.Net.Dns> .</span><span class="sxs-lookup"><span data-stu-id="74dcd-121">Some public methods of the <xref:System.Net.Sockets.Socket>, <xref:System.Net.Sockets.TcpListener>, <xref:System.Net.Sockets.TcpClient>, and <xref:System.Net.Dns> classes.</span></span>|
|`System.Net`|<span data-ttu-id="74dcd-122">Certaines méthodes publiques des <xref:System.Net.HttpWebRequest> classes, <xref:System.Net.HttpWebResponse> , <xref:System.Net.FtpWebRequest> et <xref:System.Net.FtpWebResponse> , ainsi que les informations de débogage SSL (certificats non valides, liste des émetteurs manquants et erreurs de certificat client).</span><span class="sxs-lookup"><span data-stu-id="74dcd-122">Some public methods of the <xref:System.Net.HttpWebRequest>, <xref:System.Net.HttpWebResponse>, <xref:System.Net.FtpWebRequest>, and <xref:System.Net.FtpWebResponse> classes, and SSL debug information (invalid certificates, missing issuers list, and client certificate errors).</span></span>|
|`System.Net.HttpListener`|<span data-ttu-id="74dcd-123">Certaines méthodes publiques des classes <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest> et <xref:System.Net.HttpListenerResponse>.</span><span class="sxs-lookup"><span data-stu-id="74dcd-123">Some public methods of the <xref:System.Net.HttpListener>, <xref:System.Net.HttpListenerRequest>, and <xref:System.Net.HttpListenerResponse> classes.</span></span>|
|`System.Net.Cache`|<span data-ttu-id="74dcd-124">Certaines méthodes privées et internes dans `System.Net.Cache`.</span><span class="sxs-lookup"><span data-stu-id="74dcd-124">Some private and internal methods in `System.Net.Cache`.</span></span>|
|`System.Net.Http`|<span data-ttu-id="74dcd-125">Certaines méthodes publiques des classes <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>, <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>, <xref:System.Net.Http.MessageProcessingHandler> et <xref:System.Net.Http.WebRequestHandler>.</span><span class="sxs-lookup"><span data-stu-id="74dcd-125">Some public methods of the  <xref:System.Net.Http.HttpClient>,  <xref:System.Net.Http.DelegatingHandler>,  <xref:System.Net.Http.HttpClientHandler>, <xref:System.Net.Http.HttpMessageHandler>,  <xref:System.Net.Http.MessageProcessingHandler>, and  <xref:System.Net.Http.WebRequestHandler> classes.</span></span>|
|`System.Net.WebSockets.WebSocket`|<span data-ttu-id="74dcd-126">Certaines méthodes publiques des classes <xref:System.Net.WebSockets.ClientWebSocket> et <xref:System.Net.WebSockets.WebSocket>.</span><span class="sxs-lookup"><span data-stu-id="74dcd-126">Some public methods of the <xref:System.Net.WebSockets.ClientWebSocket> and <xref:System.Net.WebSockets.WebSocket> classes.</span></span>|

### <a name="trace-output-attributes"></a><span data-ttu-id="74dcd-127">Attributs de sortie de trace</span><span class="sxs-lookup"><span data-stu-id="74dcd-127">Trace output attributes</span></span>

<span data-ttu-id="74dcd-128">Les attributs figurant dans le tableau suivant configurent la sortie de trace :</span><span class="sxs-lookup"><span data-stu-id="74dcd-128">The attributes listed in the following table configure trace output:</span></span>

|<span data-ttu-id="74dcd-129">Nom de l’attribut</span><span class="sxs-lookup"><span data-stu-id="74dcd-129">Attribute name</span></span>|<span data-ttu-id="74dcd-130">Valeur d'attribut</span><span class="sxs-lookup"><span data-stu-id="74dcd-130">Attribute value</span></span>|
|--------------------|---------------------|
|`value`|<span data-ttu-id="74dcd-131">Attribut <xref:System.String> requis.</span><span class="sxs-lookup"><span data-stu-id="74dcd-131">Required <xref:System.String> attribute.</span></span> <span data-ttu-id="74dcd-132">Définit les commentaires de la sortie.</span><span class="sxs-lookup"><span data-stu-id="74dcd-132">Sets the verbosity of the output.</span></span> <span data-ttu-id="74dcd-133">Les valeurs légitimes sont `Critical`, `Error`, `Verbose`, `Warning` et `Information`.</span><span class="sxs-lookup"><span data-stu-id="74dcd-133">Legitimate values are `Critical`, `Error`, `Verbose`, `Warning`, and `Information`.</span></span><br /><br /><span data-ttu-id="74dcd-134">Cet attribut doit être défini sur l’élément **Add** de l’élément **switches** .</span><span class="sxs-lookup"><span data-stu-id="74dcd-134">This attribute must be set on the **add** element of the **switches** element.</span></span> <span data-ttu-id="74dcd-135">Une exception est levée si cet attribut est défini sur l’élément **source** .</span><span class="sxs-lookup"><span data-stu-id="74dcd-135">An exception is thrown if this attribute is set on the **source** element.</span></span><br/><br/><span data-ttu-id="74dcd-136">Exemple : `<add name="System.Net" value="Verbose"/>`</span><span class="sxs-lookup"><span data-stu-id="74dcd-136">Example: `<add name="System.Net" value="Verbose"/>`</span></span>|
|`maxdatasize`|<span data-ttu-id="74dcd-137">Attribut <xref:System.Int32> facultatif.</span><span class="sxs-lookup"><span data-stu-id="74dcd-137">Optional <xref:System.Int32> attribute.</span></span> <span data-ttu-id="74dcd-138">Définit le nombre maximal d'octets de données réseau incluses dans chaque trace de ligne.</span><span class="sxs-lookup"><span data-stu-id="74dcd-138">Sets the maximum number of bytes of network data included in each line trace.</span></span> <span data-ttu-id="74dcd-139">La valeur par défaut est 1024.</span><span class="sxs-lookup"><span data-stu-id="74dcd-139">The default value is 1024.</span></span><br /><br /><span data-ttu-id="74dcd-140">Cet attribut doit être défini sur l’élément **source** .</span><span class="sxs-lookup"><span data-stu-id="74dcd-140">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="74dcd-141">Une exception est levée si cet attribut est défini sur un élément sous l’élément **switches** .</span><span class="sxs-lookup"><span data-stu-id="74dcd-141">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="74dcd-142">Exemple : `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="74dcd-142">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|
|`tracemode`|<span data-ttu-id="74dcd-143">Attribut <xref:System.String> facultatif.</span><span class="sxs-lookup"><span data-stu-id="74dcd-143">Optional <xref:System.String> attribute.</span></span> <span data-ttu-id="74dcd-144">Définissez la valeur `includehex` pour afficher les traces de protocole au format hexadécimal et texte.</span><span class="sxs-lookup"><span data-stu-id="74dcd-144">Set to `includehex` to show protocol traces in hexadecimal and text format.</span></span> <span data-ttu-id="74dcd-145">Définissez la valeur `protocolonly` pour afficher uniquement du texte.</span><span class="sxs-lookup"><span data-stu-id="74dcd-145">Set to `protocolonly` to show only text.</span></span> <span data-ttu-id="74dcd-146">La valeur par défaut est `includehex`.</span><span class="sxs-lookup"><span data-stu-id="74dcd-146">The default value is `includehex`.</span></span><br /><br /><span data-ttu-id="74dcd-147">Cet attribut doit être défini sur l’élément **source** .</span><span class="sxs-lookup"><span data-stu-id="74dcd-147">This attribute must be set on the **source** element.</span></span> <span data-ttu-id="74dcd-148">Une exception est levée si cet attribut est défini sur un élément sous l’élément **switches** .</span><span class="sxs-lookup"><span data-stu-id="74dcd-148">An exception is thrown if this attribute is set on an element under the **switches** element.</span></span><br/><br/><span data-ttu-id="74dcd-149">Exemple : `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span><span class="sxs-lookup"><span data-stu-id="74dcd-149">Example: `<source name="System.Net" tracemode="includehex" maxdatasize="1024">`</span></span>|

## <a name="see-also"></a><span data-ttu-id="74dcd-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74dcd-150">See also</span></span>

- [<span data-ttu-id="74dcd-151">Interprétation du suivi réseau</span><span class="sxs-lookup"><span data-stu-id="74dcd-151">Interpreting Network Tracing</span></span>](interpreting-network-tracing.md)
- [<span data-ttu-id="74dcd-152">Traçage réseau dans .NET Framework</span><span class="sxs-lookup"><span data-stu-id="74dcd-152">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
- [<span data-ttu-id="74dcd-153">Activation du traçage réseau</span><span class="sxs-lookup"><span data-stu-id="74dcd-153">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="74dcd-154">Traçage et instrumentation d'applications</span><span class="sxs-lookup"><span data-stu-id="74dcd-154">Tracing and Instrumenting Applications</span></span>](../debug-trace-profile/tracing-and-instrumenting-applications.md)
