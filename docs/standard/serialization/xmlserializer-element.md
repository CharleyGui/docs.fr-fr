---
title: Élément <xmlSerializer>
description: L' <xmlSerializer> élément spécifie si une vérification supplémentaire de la progression du XmlSerializer est effectuée.
ms.date: 03/30/2017
helpviewer_keywords:
- <xmlSerializer> element
- XML serialization, configuration
- xmlSerializer element
ms.assetid: d129d10c-3eb7-45d9-8098-5fa853825e47
ms.openlocfilehash: 68037959893ec307a896ea86d21e40a9d7aa824c
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380032"
---
# <a name="xmlserializer-element"></a><span data-ttu-id="19846-103">\<Élément> XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="19846-103">\<xmlSerializer> Element</span></span>
<span data-ttu-id="19846-104">Spécifie si un contrôle supplémentaire de la progression de <xref:System.Xml.Serialization.XmlSerializer> est effectué.</span><span class="sxs-lookup"><span data-stu-id="19846-104">Specifies whether an additional check of progress of the <xref:System.Xml.Serialization.XmlSerializer> is done.</span></span>  
  
 <span data-ttu-id="19846-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="19846-105">\<configuration></span></span>  
<span data-ttu-id="19846-106">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="19846-106">\<system.xml.serialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19846-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19846-107">Syntax</span></span>  
  
```xml  
<xmlSerializer checkDeserializerAdvance = "true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19846-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="19846-108">Attributes and Elements</span></span>  
 <span data-ttu-id="19846-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="19846-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19846-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="19846-110">Attributes</span></span>  
  
|<span data-ttu-id="19846-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="19846-111">Attribute</span></span>|<span data-ttu-id="19846-112">Description</span><span class="sxs-lookup"><span data-stu-id="19846-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19846-113">**checkDeserializeAdvances**</span><span class="sxs-lookup"><span data-stu-id="19846-113">**checkDeserializeAdvances**</span></span>|<span data-ttu-id="19846-114">Spécifie si la progression de <xref:System.Xml.Serialization.XmlSerializer> est vérifiée.</span><span class="sxs-lookup"><span data-stu-id="19846-114">Specifies whether the progress of the <xref:System.Xml.Serialization.XmlSerializer> is checked.</span></span> <span data-ttu-id="19846-115">Affectez "true" ou "false" à l'attribut.</span><span class="sxs-lookup"><span data-stu-id="19846-115">Set the attribute to "true" or "false".</span></span> <span data-ttu-id="19846-116">La valeur par défaut est "true".</span><span class="sxs-lookup"><span data-stu-id="19846-116">The default is "true".</span></span>|  
|<span data-ttu-id="19846-117">**useLegacySerializationGeneration**</span><span class="sxs-lookup"><span data-stu-id="19846-117">**useLegacySerializationGeneration**</span></span>|<span data-ttu-id="19846-118">Spécifie si <xref:System.Xml.Serialization.XmlSerializer> utilise la génération de sérialisation héritée qui génère des assemblys en écrivant le code C# dans un fichier, puis en le compilant dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="19846-118">Specifies whether the <xref:System.Xml.Serialization.XmlSerializer> uses legacy serialization generation which generates assemblies by writing C# code to a file and then compiling it to an assembly.</span></span> <span data-ttu-id="19846-119">La valeur par défaut est **false**.</span><span class="sxs-lookup"><span data-stu-id="19846-119">The default is **false**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19846-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="19846-120">Child Elements</span></span>  
 <span data-ttu-id="19846-121">Aucun.</span><span class="sxs-lookup"><span data-stu-id="19846-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19846-122">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="19846-122">Parent Elements</span></span>  
  
|<span data-ttu-id="19846-123">Élément</span><span class="sxs-lookup"><span data-stu-id="19846-123">Element</span></span>|<span data-ttu-id="19846-124">Description</span><span class="sxs-lookup"><span data-stu-id="19846-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19846-125">\<Élément System. Xml. Serialization></span><span class="sxs-lookup"><span data-stu-id="19846-125">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)|<span data-ttu-id="19846-126">Contient des paramètres de configuration pour les classes <xref:System.Xml.Serialization.XmlSerializer> et <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="19846-126">Contains configuration settings for the <xref:System.Xml.Serialization.XmlSerializer> and <xref:System.Xml.Serialization.XmlSchemaImporter> classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19846-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="19846-127">Remarks</span></span>  
 <span data-ttu-id="19846-128">Par défaut, le <xref:System.Xml.Serialization.XmlSerializer> fournit une couche supplémentaire de sécurité contre des attaques par déni de service potentielles lors de la désérialisation de données non fiables.</span><span class="sxs-lookup"><span data-stu-id="19846-128">By default, the <xref:System.Xml.Serialization.XmlSerializer> provides an additional layer of security against potential denial of service attacks when deserializing untrusted data.</span></span> <span data-ttu-id="19846-129">Pour ce faire, il tente de détecter des boucles infinies pendant la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="19846-129">It does so by attempting to detect infinite loops during deserialization.</span></span> <span data-ttu-id="19846-130">Si une telle condition est détectée, une exception est levée avec le message suivant : « Erreur interne : la désérialisation n’a pas pu avancer sur le flux de données sous-jacent. ».</span><span class="sxs-lookup"><span data-stu-id="19846-130">If such a condition is detected, an exception is thrown with the following message: "Internal error: deserialization failed to advance over underlying stream."</span></span>  
  
 <span data-ttu-id="19846-131">Le fait de recevoir ce message n'indique pas nécessairement qu'une attaque par déni de service est en cours.</span><span class="sxs-lookup"><span data-stu-id="19846-131">Receiving this message does not necessarily indicate that a denial of service attack is in progress.</span></span> <span data-ttu-id="19846-132">Dans de rares circonstances, le mécanisme de détection de boucles infinies génère un faux positif et l'exception est levée pour un message entrant légitime.</span><span class="sxs-lookup"><span data-stu-id="19846-132">In some rare circumstances, the infinite loop detection mechanism produces a false positive and the exception is thrown for a legitimate incoming message.</span></span> <span data-ttu-id="19846-133">Si vous voyez, dans votre application, que des messages légitimes sont rejetés par cette couche de protection supplémentaire, définissez l’attribut **checkDeserializeAdvances** sur la valeur false.</span><span class="sxs-lookup"><span data-stu-id="19846-133">If you find that in your particular application legitimate messages are being rejected by this extra layer of protection, set **checkDeserializeAdvances** attribute to "false".</span></span>  
  
## <a name="example"></a><span data-ttu-id="19846-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="19846-134">Example</span></span>  
 <span data-ttu-id="19846-135">L’exemple de code suivant assigne la valeur false à l’attribut **checkDeserializeAdvances**.</span><span class="sxs-lookup"><span data-stu-id="19846-135">The following code example sets the **checkDeserializeAdvances** attribute to "false".</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="19846-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19846-136">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="19846-137">\<Élément System. Xml. Serialization></span><span class="sxs-lookup"><span data-stu-id="19846-137">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="19846-138">Sérialisation XML et SOAP</span><span class="sxs-lookup"><span data-stu-id="19846-138">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
