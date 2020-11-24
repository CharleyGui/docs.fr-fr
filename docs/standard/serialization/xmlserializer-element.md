---
title: Élément <xmlSerializer>
description: L' <xmlSerializer> élément spécifie si une vérification supplémentaire de la progression du XmlSerializer est effectuée.
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 6f368880c97a21dc3e9593ecb2319d265a1b8932
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676489"
---
# <a name="xmlserializer-element"></a><span data-ttu-id="e3709-103">Élément \<xmlSerializer></span><span class="sxs-lookup"><span data-stu-id="e3709-103">\<xmlSerializer> Element</span></span>

<span data-ttu-id="e3709-104">Spécifie si un contrôle supplémentaire de la progression de <xref:System.Xml.Serialization.XmlSerializer> est effectué.</span><span class="sxs-lookup"><span data-stu-id="e3709-104">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 \<configuration>  
\<system.xml.serialization>  
  
## <a name="syntax"></a><span data-ttu-id="e3709-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e3709-105">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3709-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e3709-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e3709-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e3709-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3709-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="e3709-108">Attributes</span></span>  
  
|<span data-ttu-id="e3709-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="e3709-109">Attribute</span></span>|<span data-ttu-id="e3709-110">Description</span><span class="sxs-lookup"><span data-stu-id="e3709-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3709-111">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="e3709-111">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="e3709-112">Spécifie si la progression de <xref:System.Xml.Serialization.XmlSerializer> est vérifiée.</span><span class="sxs-lookup"><span data-stu-id="e3709-112">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="e3709-113">Affectez "true" ou "false" à l'attribut.</span><span class="sxs-lookup"><span data-stu-id="e3709-113">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="e3709-114">La valeur par défaut est "true".</span><span class="sxs-lookup"><span data-stu-id="e3709-114">The default is "true".</span></span>|  
|<span data-ttu-id="e3709-115">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="e3709-115">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="e3709-116">Spécifie si <xref:System.Xml.Serialization.XmlSerializer> utilise la génération de sérialisation héritée qui génère des assemblys en écrivant le code C# dans un fichier, puis en le compilant dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="e3709-116">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="e3709-117">La valeur par défaut est **false**.</span><span class="sxs-lookup"><span data-stu-id="e3709-117">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3709-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e3709-118">Child Elements</span></span>  

 <span data-ttu-id="e3709-119">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e3709-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e3709-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e3709-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e3709-121">Élément</span><span class="sxs-lookup"><span data-stu-id="e3709-121">Element</span></span>|<span data-ttu-id="e3709-122">Description</span><span class="sxs-lookup"><span data-stu-id="e3709-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e3709-123">\<system.xml.serialization> Appartient</span><span class="sxs-lookup"><span data-stu-id="e3709-123">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)|<span data-ttu-id="e3709-124">Contient des paramètres de configuration pour les classes <xref:System.Xml.Serialization.XmlSerializer> et <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="e3709-124">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3709-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="e3709-125">Remarks</span></span>  

 <span data-ttu-id="e3709-126">Par défaut, le <xref:System.Xml.Serialization.XmlSerializer> fournit une couche supplémentaire de sécurité contre des attaques par déni de service potentielles lors de la désérialisation de données non fiables.</span><span class="sxs-lookup"><span data-stu-id="e3709-126">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="e3709-127">Pour ce faire, il tente de détecter des boucles infinies pendant la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="e3709-127">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="e3709-128">Si une telle condition est détectée, une exception est levée avec le message suivant : « Erreur interne : la désérialisation n’a pas pu avancer sur le flux de données sous-jacent. ».</span><span class="sxs-lookup"><span data-stu-id="e3709-128">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="e3709-129">Le fait de recevoir ce message n'indique pas nécessairement qu'une attaque par déni de service est en cours.</span><span class="sxs-lookup"><span data-stu-id="e3709-129">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="e3709-130">Dans de rares circonstances, le mécanisme de détection de boucles infinies génère un faux positif et l'exception est levée pour un message entrant légitime.</span><span class="sxs-lookup"><span data-stu-id="e3709-130">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="e3709-131">Si vous voyez, dans votre application, que des messages légitimes sont rejetés par cette couche de protection supplémentaire, définissez l’attribut **checkDeserializeAdvances** sur la valeur false.</span><span class="sxs-lookup"><span data-stu-id="e3709-131">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3709-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="e3709-132">Example</span></span>  

 <span data-ttu-id="e3709-133">L’exemple de code suivant assigne la valeur false à l’attribut **checkDeserializeAdvances**.</span><span class="sxs-lookup"><span data-stu-id="e3709-133">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3709-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3709-134">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="e3709-135">\<system.xml.serialization> Appartient</span><span class="sxs-lookup"><span data-stu-id="e3709-135">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
- [<span data-ttu-id="e3709-136">Sérialisation XML et SOAP</span><span class="sxs-lookup"><span data-stu-id="e3709-136">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
