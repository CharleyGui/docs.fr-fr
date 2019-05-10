---
title: Référence des schémas de contrats de données
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: d7797b7a8786a89671175bccb501b7fe69c021d7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627072"
---
# <a name="data-contract-schema-reference"></a><span data-ttu-id="3177e-102">Référence des schémas de contrats de données</span><span class="sxs-lookup"><span data-stu-id="3177e-102">Data Contract Schema Reference</span></span>
<span data-ttu-id="3177e-103">Cette rubrique décrit le sous-ensemble du schéma XML (XSD) utilisé par <xref:System.Runtime.Serialization.DataContractSerializer> pour décrire les types CLR (Common Language Run-time) pour la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="3177e-103">This topic describes the subset of the XML Schema (XSD) used by <xref:System.Runtime.Serialization.DataContractSerializer> to describe common language runtime (CLR) types for XML serialization.</span></span>  
  
## <a name="datacontractserializer-mappings"></a><span data-ttu-id="3177e-104">Mappages DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="3177e-104">DataContractSerializer Mappings</span></span>  
 <span data-ttu-id="3177e-105">Le `DataContractSerializer` mappe des types CLR à XSD lorsque les métadonnées sont exportées à partir d’un service Windows Communication Foundation (WCF) à l’aide d’un point de terminaison de métadonnées ou le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3177e-105">The `DataContractSerializer` maps CLR types to XSD when metadata is exported from a Windows Communication Foundation (WCF) service using a metadata endpoint or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="3177e-106">Pour plus d’informations, consultez [Data Contract Serializer](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span><span class="sxs-lookup"><span data-stu-id="3177e-106">For more information, see [Data Contract Serializer](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span></span>  
  
 <span data-ttu-id="3177e-107">`DataContractSerializer` mappe également XSD aux types CLR lorsque Svcutil.exe est utilisé pour accéder à Web Services Description Language (WSDL) ou aux documents XSD et génère des contrats de données pour les services ou les clients.</span><span class="sxs-lookup"><span data-stu-id="3177e-107">The `DataContractSerializer` also maps XSD to CLR types when Svcutil.exe is used to access Web Services Description Language (WSDL) or XSD documents and generate data contracts for services or clients.</span></span>  
  
 <span data-ttu-id="3177e-108">Uniquement les instances de schéma XML conformes aux spécifications déclarées dans ce document peuvent être mappées aux types CLR à l'aide de `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="3177e-108">Only XML Schema instances that conform to requirements stated in this document can be mapped to CLR types using `DataContractSerializer`.</span></span>  
  
### <a name="support-levels"></a><span data-ttu-id="3177e-109">Niveaux pris en charge</span><span class="sxs-lookup"><span data-stu-id="3177e-109">Support Levels</span></span>  
 <span data-ttu-id="3177e-110">`DataContractSerializer` fournit les niveaux de prise en charge suivants pour une fonctionnalité de schéma XML donnée :</span><span class="sxs-lookup"><span data-stu-id="3177e-110">The `DataContractSerializer` provides the following levels of support for a given XML Schema feature:</span></span>  
  
- <span data-ttu-id="3177e-111">**Pris en charge**.</span><span class="sxs-lookup"><span data-stu-id="3177e-111">**Supported**.</span></span> <span data-ttu-id="3177e-112">Il y a mappage explicite de cette fonctionnalité aux types ou aux attributs CLR (ou les deux à la fois) via `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="3177e-112">There is explicit mapping from this feature to CLR types or attributes (or both) using `DataContractSerializer`.</span></span>  
  
- <span data-ttu-id="3177e-113">**Ignoré**.</span><span class="sxs-lookup"><span data-stu-id="3177e-113">**Ignored**.</span></span> <span data-ttu-id="3177e-114">La fonctionnalité est autorisée dans les schémas importés par `DataContractSerializer`, mais n'a aucun effet sur la génération du code.</span><span class="sxs-lookup"><span data-stu-id="3177e-114">The feature is allowed in schemas imported by the `DataContractSerializer`, but has no effect on code generation.</span></span>  
  
- <span data-ttu-id="3177e-115">**Interdit**.</span><span class="sxs-lookup"><span data-stu-id="3177e-115">**Forbidden**.</span></span> <span data-ttu-id="3177e-116">`DataContractSerializer` ne prend pas en charge l'importation d'un schéma à l'aide de la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="3177e-116">The `DataContractSerializer` does not support importing a schema using the feature.</span></span> <span data-ttu-id="3177e-117">Par exemple, Svcutil.exe, lors de l'accès à un WSDL avec un schéma qui utilise une telle fonctionnalité, revient à la place à l'utilisation de <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="3177e-117">For example, Svcutil.exe, when accessing a WSDL with a schema that uses such a feature, falls back to using the <xref:System.Xml.Serialization.XmlSerializer> instead.</span></span> <span data-ttu-id="3177e-118">La valeur est par défaut.</span><span class="sxs-lookup"><span data-stu-id="3177e-118">This is by default.</span></span>  
  
## <a name="general-information"></a><span data-ttu-id="3177e-119">Informations générales</span><span class="sxs-lookup"><span data-stu-id="3177e-119">General Information</span></span>  
  
- <span data-ttu-id="3177e-120">L’espace de noms du schéma est décrit sur la page [XML Schema](https://go.microsoft.com/fwlink/?LinkId=95475)(Schéma XML).</span><span class="sxs-lookup"><span data-stu-id="3177e-120">The schema namespace is described at [XML Schema](https://go.microsoft.com/fwlink/?LinkId=95475).</span></span> <span data-ttu-id="3177e-121">Le préfixe "xs" est utilisé dans ce document.</span><span class="sxs-lookup"><span data-stu-id="3177e-121">The prefix "xs" is used in this document.</span></span>  
  
- <span data-ttu-id="3177e-122">Les attributs avec un espace de noms qui n'est pas un schéma sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="3177e-122">Any attributes with a non-schema namespace are ignored.</span></span>  
  
- <span data-ttu-id="3177e-123">Les annotations (sauf celles décrites dans ce document) sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="3177e-123">Any annotations (except for those described in this document) are ignored.</span></span>  
  
### <a name="xsschema-attributes"></a><span data-ttu-id="3177e-124">\<xs : Schema > : attributs</span><span class="sxs-lookup"><span data-stu-id="3177e-124">\<xs:schema>: attributes</span></span>  
  
|<span data-ttu-id="3177e-125">Attribut</span><span class="sxs-lookup"><span data-stu-id="3177e-125">Attribute</span></span>|<span data-ttu-id="3177e-126">DataContract</span><span class="sxs-lookup"><span data-stu-id="3177e-126">DataContract</span></span>|  
|---------------|------------------|  
|`attributeFormDefault`|<span data-ttu-id="3177e-127">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-127">Ignored.</span></span>|  
|`blockDefault`|<span data-ttu-id="3177e-128">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-128">Ignored.</span></span>|  
|`elementFormDefault`|<span data-ttu-id="3177e-129">Doit être qualifié.</span><span class="sxs-lookup"><span data-stu-id="3177e-129">Must be qualified.</span></span> <span data-ttu-id="3177e-130">Tous les éléments doivent être qualifiés pour qu'un schéma soit pris en charge par `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="3177e-130">All elements must be qualified for a schema to be supported by `DataContractSerializer`.</span></span> <span data-ttu-id="3177e-131">Cela est possible en affectant xs:schema/@elementFormDefault sur « qualified » ou en définissant xs:element/@form « qualified » sur chaque déclaration d’élément individuelle.</span><span class="sxs-lookup"><span data-stu-id="3177e-131">This can be accomplished by either setting xs:schema/@elementFormDefault to "qualified" or by setting xs:element/@form to "qualified" on each individual element declaration.</span></span>|  
|`finalDefault`|<span data-ttu-id="3177e-132">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-132">Ignored.</span></span>|  
|`Id`|<span data-ttu-id="3177e-133">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-133">Ignored.</span></span>|  
|`targetNamespace`|<span data-ttu-id="3177e-134">Pris en charge et mappé à l'espace de noms du contrat de données.</span><span class="sxs-lookup"><span data-stu-id="3177e-134">Supported and mapped to the data contract namespace.</span></span> <span data-ttu-id="3177e-135">Si cet attribut n'est pas spécifié, l'espace de noms vierge est utilisé.</span><span class="sxs-lookup"><span data-stu-id="3177e-135">If this attribute is not specified, the blank namespace is used.</span></span> <span data-ttu-id="3177e-136">Ne peut pas être l’espace de noms réservé `http://schemas.microsoft.com/2003/10/Serialization/`.</span><span class="sxs-lookup"><span data-stu-id="3177e-136">Cannot be the reserved namespace `http://schemas.microsoft.com/2003/10/Serialization/`.</span></span>|  
|`version`|<span data-ttu-id="3177e-137">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-137">Ignored.</span></span>|  
  
### <a name="xsschema-contents"></a><span data-ttu-id="3177e-138">\<xs : Schema > : contenu</span><span class="sxs-lookup"><span data-stu-id="3177e-138">\<xs:schema>: contents</span></span>  
  
|<span data-ttu-id="3177e-139">Sommaire</span><span class="sxs-lookup"><span data-stu-id="3177e-139">Contents</span></span>|<span data-ttu-id="3177e-140">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-140">Schema</span></span>|  
|--------------|------------|  
|`include`|<span data-ttu-id="3177e-141">Prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-141">Supported.</span></span> <span data-ttu-id="3177e-142">`DataContractSerializer` prend en charge xs:include et xs:import.</span><span class="sxs-lookup"><span data-stu-id="3177e-142">`DataContractSerializer` supports xs:include and xs:import.</span></span> <span data-ttu-id="3177e-143">Toutefois, Svcutil.exe restreint le suivi des références `xs:include/@schemaLocation` et `xs:import/@location` lorsque les métadonnées sont chargées à partir d'un fichier local.</span><span class="sxs-lookup"><span data-stu-id="3177e-143">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="3177e-144">La liste des fichiers de schéma doit passer par un mécanisme hors bande et non par `include` dans ce cas ; les documents de schéma `include`sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="3177e-144">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|  
|`redefine`|<span data-ttu-id="3177e-145">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-145">Forbidden.</span></span> <span data-ttu-id="3177e-146">L'utilisation de `xs:redefine` est interdite par `DataContractSerializer` pour des raisons de sécurité : `x:redefine` requiert que `schemaLocation` soit suivi.</span><span class="sxs-lookup"><span data-stu-id="3177e-146">The use of `xs:redefine` is forbidden by `DataContractSerializer` for security reasons: `x:redefine` requires `schemaLocation` to be followed.</span></span> <span data-ttu-id="3177e-147">Dans certaines circonstances, Svcutil.exe restreint l'utilisation de `schemaLocation`à l'aide de DataContract.</span><span class="sxs-lookup"><span data-stu-id="3177e-147">In certain circumstances, Svcutil.exe using DataContract restricts use of `schemaLocation`.</span></span>|  
|`import`|<span data-ttu-id="3177e-148">Prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-148">Supported.</span></span> <span data-ttu-id="3177e-149">`DataContractSerializer` prend en charge `xs:include` et `xs:import`.</span><span class="sxs-lookup"><span data-stu-id="3177e-149">`DataContractSerializer` supports `xs:include` and `xs:import`.</span></span> <span data-ttu-id="3177e-150">Toutefois, Svcutil.exe restreint le suivi des références `xs:include/@schemaLocation` et `xs:import/@location` lorsque les métadonnées sont chargées à partir d'un fichier local.</span><span class="sxs-lookup"><span data-stu-id="3177e-150">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="3177e-151">La liste des fichiers de schéma doit passer par un mécanisme hors bande et non par `include` dans ce cas ; les documents de schéma `include`sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="3177e-151">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|  
|`simpleType`|<span data-ttu-id="3177e-152">Prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-152">Supported.</span></span> <span data-ttu-id="3177e-153">Consultez la section `xs:simpleType` .</span><span class="sxs-lookup"><span data-stu-id="3177e-153">See the `xs:simpleType` section.</span></span>|  
|`complexType`|<span data-ttu-id="3177e-154">Pris en charge, mappe aux contrats de données.</span><span class="sxs-lookup"><span data-stu-id="3177e-154">Supported, maps to data contracts.</span></span> <span data-ttu-id="3177e-155">Consultez la section `xs:complexType` .</span><span class="sxs-lookup"><span data-stu-id="3177e-155">See the `xs:complexType` section.</span></span>|  
|`group`|<span data-ttu-id="3177e-156">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-156">Ignored.</span></span> <span data-ttu-id="3177e-157">`DataContractSerializer` ne prend pas en charge l'utilisation de `xs:group`, `xs:attributeGroup`et `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="3177e-157">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="3177e-158">Ces déclarations sont ignorées en tant qu'enfants de `xs:schema`, mais ne peuvent pas être référencées à partir de `complexType` ou d'autres constructions prises en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-158">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`attributeGroup`|<span data-ttu-id="3177e-159">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-159">Ignored.</span></span> <span data-ttu-id="3177e-160">`DataContractSerializer` ne prend pas en charge l'utilisation de `xs:group`, `xs:attributeGroup`et `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="3177e-160">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="3177e-161">Ces déclarations sont ignorées en tant qu'enfants de `xs:schema`, mais ne peuvent pas être référencées à partir de `complexType` ou d'autres constructions prises en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-161">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`element`|<span data-ttu-id="3177e-162">Prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-162">Supported.</span></span> <span data-ttu-id="3177e-163">Consultez la déclaration d'élément globale (GED).</span><span class="sxs-lookup"><span data-stu-id="3177e-163">See Global Element Declaration (GED).</span></span>|  
|`attribute`|<span data-ttu-id="3177e-164">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-164">Ignored.</span></span> <span data-ttu-id="3177e-165">`DataContractSerializer` ne prend pas en charge l'utilisation de `xs:group`, `xs:attributeGroup`et `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="3177e-165">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="3177e-166">Ces déclarations sont ignorées en tant qu'enfants de `xs:schema`, mais ne peuvent pas être référencées à partir de `complexType` ou d'autres constructions prises en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-166">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`notation`|<span data-ttu-id="3177e-167">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-167">Ignored.</span></span>|  
  
## <a name="complex-types--xscomplextype"></a><span data-ttu-id="3177e-168">Les Types complexes – \<xs : complexType ></span><span class="sxs-lookup"><span data-stu-id="3177e-168">Complex Types – \<xs:complexType></span></span>  
  
### <a name="general-information"></a><span data-ttu-id="3177e-169">Informations générales</span><span class="sxs-lookup"><span data-stu-id="3177e-169">General Information</span></span>  
 <span data-ttu-id="3177e-170">Chaque type complexe \<xs : complexType > mappe à un contrat de données.</span><span class="sxs-lookup"><span data-stu-id="3177e-170">Each complex type \<xs:complexType> maps to a data contract.</span></span>  
  
### <a name="xscomplextype-attributes"></a><span data-ttu-id="3177e-171">\<xs : complexType > : attributs</span><span class="sxs-lookup"><span data-stu-id="3177e-171">\<xs:complexType>: attributes</span></span>  
  
|<span data-ttu-id="3177e-172">Attribut</span><span class="sxs-lookup"><span data-stu-id="3177e-172">Attribute</span></span>|<span data-ttu-id="3177e-173">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-173">Schema</span></span>|  
|---------------|------------|  
|`abstract`|<span data-ttu-id="3177e-174">Doit être faux (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="3177e-174">Must be false (default).</span></span>|  
|`block`|<span data-ttu-id="3177e-175">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-175">Forbidden.</span></span>|  
|`final`|<span data-ttu-id="3177e-176">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-176">Ignored.</span></span>|  
|`id`|<span data-ttu-id="3177e-177">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-177">Ignored.</span></span>|  
|`mixed`|<span data-ttu-id="3177e-178">Doit être faux (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="3177e-178">Must be false (default).</span></span>|  
|`name`|<span data-ttu-id="3177e-179">Pris en charge et mappé au nom du contrat de données.</span><span class="sxs-lookup"><span data-stu-id="3177e-179">Supported and mapped to the data contract name.</span></span> <span data-ttu-id="3177e-180">Si le nom inclut des points, une tentative est faite pour mapper le type à un type interne.</span><span class="sxs-lookup"><span data-stu-id="3177e-180">If there are periods in the name, an attempt is made to map the type to an inner type.</span></span> <span data-ttu-id="3177e-181">Par exemple, un type complexe nommé `A.B` mappe à un type de contrat de données qui est un type interne d'un type portant le nom du contrat de données `A`, mais uniquement si un tel type de contrat de données existe.</span><span class="sxs-lookup"><span data-stu-id="3177e-181">For example, a complex type named `A.B` maps to a data contract type that is an inner type of a type with the data contract name `A`, but only if such a data contract type exists.</span></span> <span data-ttu-id="3177e-182">Plusieurs niveaux d'imbrication sont possibles : par exemple, `A.B.C` peut être un type interne, mais uniquement si à la fois `A` et `A.B` existent.</span><span class="sxs-lookup"><span data-stu-id="3177e-182">More than one level of nesting is possible: for example, `A.B.C` can be an inner type, but only if `A` and `A.B` both exist.</span></span>|  
  
### <a name="xscomplextype-contents"></a><span data-ttu-id="3177e-183">\<xs : complexType > : contenu</span><span class="sxs-lookup"><span data-stu-id="3177e-183">\<xs:complexType>: contents</span></span>  
  
|<span data-ttu-id="3177e-184">Sommaire</span><span class="sxs-lookup"><span data-stu-id="3177e-184">Contents</span></span>|<span data-ttu-id="3177e-185">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-185">Schema</span></span>|  
|--------------|------------|  
|`simpleContent`|<span data-ttu-id="3177e-186">Les extensions sont interdites.</span><span class="sxs-lookup"><span data-stu-id="3177e-186">Extensions are forbidden.</span></span><br /><br /> <span data-ttu-id="3177e-187">La restriction est autorisée uniquement depuis `anySimpleType`.</span><span class="sxs-lookup"><span data-stu-id="3177e-187">Restriction is allowed only from `anySimpleType`.</span></span>|  
|`complexContent`|<span data-ttu-id="3177e-188">Prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-188">Supported.</span></span> <span data-ttu-id="3177e-189">Consultez « Héritage ».</span><span class="sxs-lookup"><span data-stu-id="3177e-189">See "Inheritance".</span></span>|  
|`group`|<span data-ttu-id="3177e-190">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-190">Forbidden.</span></span>|  
|`all`|<span data-ttu-id="3177e-191">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-191">Forbidden.</span></span>|  
|`choice`|<span data-ttu-id="3177e-192">Interdit</span><span class="sxs-lookup"><span data-stu-id="3177e-192">Forbidden</span></span>|  
|`sequence`|<span data-ttu-id="3177e-193">Pris en charge, mappe aux membres de données d'un contrat de données.</span><span class="sxs-lookup"><span data-stu-id="3177e-193">Supported, maps to data members of a data contract.</span></span>|  
|`attribute`|<span data-ttu-id="3177e-194">Interdit, même si l'utilisation = "prohibited" (avec une exception).</span><span class="sxs-lookup"><span data-stu-id="3177e-194">Forbidden, even if use="prohibited" (with one exception).</span></span> <span data-ttu-id="3177e-195">Uniquement les attributs facultatifs de l'espace de noms du schéma de sérialisation standard sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-195">Only optional attributes from the Standard Serialization Schema namespace are supported.</span></span> <span data-ttu-id="3177e-196">Ils ne mappent pas aux membres de données dans le modèle de programmation du contrat de données.</span><span class="sxs-lookup"><span data-stu-id="3177e-196">They do not map to data members in the data contract programming model.</span></span> <span data-ttu-id="3177e-197">Actuellement, un seul de ces attributs est significatif et est discuté dans la section ISerializable.</span><span class="sxs-lookup"><span data-stu-id="3177e-197">Currently, only one such attribute has meaning and is discussed in the ISerializable section.</span></span> <span data-ttu-id="3177e-198">Tous les autres sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="3177e-198">All others are ignored.</span></span>|  
|`attributeGroup`|<span data-ttu-id="3177e-199">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-199">Forbidden.</span></span> <span data-ttu-id="3177e-200">Dans la version v1 WCF, `DataContractSerializer` ignore la présence de `attributeGroup` dans `xs:complexType`.</span><span class="sxs-lookup"><span data-stu-id="3177e-200">In the WCF v1 release, `DataContractSerializer` ignores the presence of `attributeGroup` inside `xs:complexType`.</span></span>|  
|`anyAttribute`|<span data-ttu-id="3177e-201">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-201">Forbidden.</span></span>|  
|<span data-ttu-id="3177e-202">(vide)</span><span class="sxs-lookup"><span data-stu-id="3177e-202">(empty)</span></span>|<span data-ttu-id="3177e-203">Mappe à un contrat de données sans membres de données.</span><span class="sxs-lookup"><span data-stu-id="3177e-203">Maps to a data contract with no data members.</span></span>|  
  
### <a name="xssequence-in-a-complex-type-attributes"></a><span data-ttu-id="3177e-204">\<xs : sequence > dans un type complexe : attributs</span><span class="sxs-lookup"><span data-stu-id="3177e-204">\<xs:sequence> in a complex type: attributes</span></span>  
  
|<span data-ttu-id="3177e-205">Attribut</span><span class="sxs-lookup"><span data-stu-id="3177e-205">Attribute</span></span>|<span data-ttu-id="3177e-206">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-206">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="3177e-207">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-207">Ignored.</span></span>|  
|`maxOccurs`|<span data-ttu-id="3177e-208">Doit être 1 (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="3177e-208">Must be 1 (default).</span></span>|  
|`minOccurs`|<span data-ttu-id="3177e-209">Doit être 1 (valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="3177e-209">Must be 1 (default).</span></span>|  
  
### <a name="xssequence-in-a-complex-type-contents"></a><span data-ttu-id="3177e-210">\<xs : sequence > dans un type complexe : contenu</span><span class="sxs-lookup"><span data-stu-id="3177e-210">\<xs:sequence> in a complex type: contents</span></span>  
  
|<span data-ttu-id="3177e-211">Sommaire</span><span class="sxs-lookup"><span data-stu-id="3177e-211">Contents</span></span>|<span data-ttu-id="3177e-212">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-212">Schema</span></span>|  
|--------------|------------|  
|`element`|<span data-ttu-id="3177e-213">Chaque instance mappe à un membre de données.</span><span class="sxs-lookup"><span data-stu-id="3177e-213">Each instance maps to a data member.</span></span>|  
|`group`|<span data-ttu-id="3177e-214">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-214">Forbidden.</span></span>|  
|`choice`|<span data-ttu-id="3177e-215">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-215">Forbidden.</span></span>|  
|`sequence`|<span data-ttu-id="3177e-216">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-216">Forbidden.</span></span>|  
|`any`|<span data-ttu-id="3177e-217">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-217">Forbidden.</span></span>|  
|<span data-ttu-id="3177e-218">(vide)</span><span class="sxs-lookup"><span data-stu-id="3177e-218">(empty)</span></span>|<span data-ttu-id="3177e-219">Mappe à un contrat de données sans membres de données.</span><span class="sxs-lookup"><span data-stu-id="3177e-219">Maps to a data contract with no data members.</span></span>|  
  
## <a name="elements--xselement"></a><span data-ttu-id="3177e-220">Éléments – \<xs : element ></span><span class="sxs-lookup"><span data-stu-id="3177e-220">Elements – \<xs:element></span></span>  
  
### <a name="general-information"></a><span data-ttu-id="3177e-221">Informations générales</span><span class="sxs-lookup"><span data-stu-id="3177e-221">General Information</span></span>  
 <span data-ttu-id="3177e-222">`<xs:element>` peut se produire dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="3177e-222">`<xs:element>` can occur in the following contexts:</span></span>  
  
- <span data-ttu-id="3177e-223">Il peut se produire dans un `<xs:sequence>`, qui décrit un membre de données d'un contrat de données normal (qui n'est pas une collection).</span><span class="sxs-lookup"><span data-stu-id="3177e-223">It can occur within an `<xs:sequence>`, which describes a data member of a regular (non-collection) data contract.</span></span> <span data-ttu-id="3177e-224">Dans ce cas, l'attribut `maxOccurs` doit avoir la valeur 1.</span><span class="sxs-lookup"><span data-stu-id="3177e-224">In this case, the `maxOccurs` attribute must be 1.</span></span> <span data-ttu-id="3177e-225">(Une valeur de 0 n'est pas autorisée).</span><span class="sxs-lookup"><span data-stu-id="3177e-225">(A value of 0 is not allowed).</span></span>  
  
- <span data-ttu-id="3177e-226">Il peut se produire dans un `<xs:sequence>`, qui décrit un membre de données d'un contrat de données de collection.</span><span class="sxs-lookup"><span data-stu-id="3177e-226">It can occur within an `<xs:sequence>`, which describes a data member of a collection data contract.</span></span> <span data-ttu-id="3177e-227">Dans ce cas, l'attribut `maxOccurs` doit être supérieur à 1 ou « unbounded ».</span><span class="sxs-lookup"><span data-stu-id="3177e-227">In this case, the `maxOccurs` attribute must be greater than 1 or "unbounded".</span></span>  
  
- <span data-ttu-id="3177e-228">Il peut se produire dans un `<xs:schema>` en tant que déclaration d'élément globale (GED).</span><span class="sxs-lookup"><span data-stu-id="3177e-228">It can occur within an `<xs:schema>` as a Global Element Declaration (GED).</span></span>  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a><span data-ttu-id="3177e-229">\<xs : element > avec maxOccurs = 1 dans un \<xs : sequence > (données membres)</span><span class="sxs-lookup"><span data-stu-id="3177e-229">\<xs:element> with maxOccurs=1 within an \<xs:sequence> (Data Members)</span></span>  
  
|<span data-ttu-id="3177e-230">Attribut</span><span class="sxs-lookup"><span data-stu-id="3177e-230">Attribute</span></span>|<span data-ttu-id="3177e-231">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-231">Schema</span></span>|  
|---------------|------------|  
|`ref`|<span data-ttu-id="3177e-232">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-232">Forbidden.</span></span>|  
|`name`|<span data-ttu-id="3177e-233">Pris en charge, mappe au nom du membre de données.</span><span class="sxs-lookup"><span data-stu-id="3177e-233">Supported, maps to the data member name.</span></span>|  
|`type`|<span data-ttu-id="3177e-234">Pris en charge, mappe au type du membre de données.</span><span class="sxs-lookup"><span data-stu-id="3177e-234">Supported, maps to the data member type.</span></span> <span data-ttu-id="3177e-235">Pour plus d'informations, consultez le mappage de type/primitif.</span><span class="sxs-lookup"><span data-stu-id="3177e-235">For more information, see Type/primitive mapping.</span></span> <span data-ttu-id="3177e-236">Si non spécifié (et l'élément ne contient pas de type anonyme), `xs:anyType` est pris en compte.</span><span class="sxs-lookup"><span data-stu-id="3177e-236">If not specified (and the element does not contain an anonymous type), `xs:anyType` is assumed.</span></span>|  
|`block`|<span data-ttu-id="3177e-237">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-237">Ignored.</span></span>|  
|`default`|<span data-ttu-id="3177e-238">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-238">Forbidden.</span></span>|  
|`fixed`|<span data-ttu-id="3177e-239">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-239">Forbidden.</span></span>|  
|`form`|<span data-ttu-id="3177e-240">Doit être qualifié.</span><span class="sxs-lookup"><span data-stu-id="3177e-240">Must be qualified.</span></span> <span data-ttu-id="3177e-241">Cet attribut peut également être défini via `elementFormDefault` sur `xs:schema`.</span><span class="sxs-lookup"><span data-stu-id="3177e-241">This attribute can be set through `elementFormDefault` on `xs:schema`.</span></span>|  
|`id`|<span data-ttu-id="3177e-242">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-242">Ignored.</span></span>|  
|`maxOccurs`|<span data-ttu-id="3177e-243">1</span><span class="sxs-lookup"><span data-stu-id="3177e-243">1</span></span>|  
|`minOccurs`|<span data-ttu-id="3177e-244">Mappe à la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> d'un membre de données (`IsRequired` a la valeur true lorsque `minOccurs` a la valeur 1).</span><span class="sxs-lookup"><span data-stu-id="3177e-244">Maps to the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of a data member (`IsRequired` is true when `minOccurs` is 1).</span></span>|  
|`nillable`|<span data-ttu-id="3177e-245">Affecte le mappage de type.</span><span class="sxs-lookup"><span data-stu-id="3177e-245">Affects type mapping.</span></span> <span data-ttu-id="3177e-246">Consultez le mappage de type/primitif.</span><span class="sxs-lookup"><span data-stu-id="3177e-246">See Type/primitive mapping.</span></span>|  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a><span data-ttu-id="3177e-247">\<xs : element > avec maxOccurs > 1 dans un \<xs : sequence > (Collections)</span><span class="sxs-lookup"><span data-stu-id="3177e-247">\<xs:element> with maxOccurs>1 within an \<xs:sequence> (Collections)</span></span>  
  
- <span data-ttu-id="3177e-248">Mappe à un <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3177e-248">Maps to a <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span></span>  
  
- <span data-ttu-id="3177e-249">Dans les types collection, un seul xs:element est autorisé dans un xs:sequence.</span><span class="sxs-lookup"><span data-stu-id="3177e-249">In collection types, only one xs:element is allowed within an xs:sequence.</span></span>  
  
 <span data-ttu-id="3177e-250">Les collections peuvent appartenir aux types suivants :</span><span class="sxs-lookup"><span data-stu-id="3177e-250">Collections can be of the following types:</span></span>  
  
- <span data-ttu-id="3177e-251">Collections normales (par exemple, tableaux).</span><span class="sxs-lookup"><span data-stu-id="3177e-251">Regular collections (for example, arrays).</span></span>  
  
- <span data-ttu-id="3177e-252">Collections de dictionnaires (mappage d'une valeur à une autre; par exemple, un <xref:System.Collections.Hashtable>).</span><span class="sxs-lookup"><span data-stu-id="3177e-252">Dictionary collections (mapping one value to another; for example, a <xref:System.Collections.Hashtable>).</span></span>  
  
- <span data-ttu-id="3177e-253">La seule différence entre un dictionnaire et un tableau pour un type de paire clé/valeur réside dans le modèle de programmation généré.</span><span class="sxs-lookup"><span data-stu-id="3177e-253">The only difference between a dictionary and an array of a key/value pair type is in the generated programming model.</span></span> <span data-ttu-id="3177e-254">Il existe un mécanisme d'annotation de schéma qui peut être utilisé pour indiquer qu'un type donné est une collection de dictionnaires.</span><span class="sxs-lookup"><span data-stu-id="3177e-254">There is a schema annotation mechanism that can be used to indicate that a given type is a dictionary collection.</span></span>  
  
 <span data-ttu-id="3177e-255">Les règles appliquées aux attributs `ref`, `block`, `default`, `fixed`, `form`et `id` sont les mêmes que pour le type qui n'est pas une collection.</span><span class="sxs-lookup"><span data-stu-id="3177e-255">The rules for the `ref`, `block`, `default`, `fixed`, `form`, and `id` attributes are the same as for the non-collection case.</span></span> <span data-ttu-id="3177e-256">Les autres attributs sont inclus dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="3177e-256">Other attributes include those in the following table.</span></span>  
  
|<span data-ttu-id="3177e-257">Attribut</span><span class="sxs-lookup"><span data-stu-id="3177e-257">Attribute</span></span>|<span data-ttu-id="3177e-258">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-258">Schema</span></span>|  
|---------------|------------|  
|`name`|<span data-ttu-id="3177e-259">Pris en charge, mappe à la propriété <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> dans l'attribut `CollectionDataContractAttribute` .</span><span class="sxs-lookup"><span data-stu-id="3177e-259">Supported, maps to the <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> property in the `CollectionDataContractAttribute` attribute.</span></span>|  
|`type`|<span data-ttu-id="3177e-260">Pris en charge, mappe au type stocké dans la collection.</span><span class="sxs-lookup"><span data-stu-id="3177e-260">Supported, maps to the type stored in the collection.</span></span>|  
|`maxOccurs`|<span data-ttu-id="3177e-261">Supérieur à 1 ou "unbounded".</span><span class="sxs-lookup"><span data-stu-id="3177e-261">Greater than 1 or "unbounded".</span></span> <span data-ttu-id="3177e-262">Le schéma DC doit utiliser "unbounded".</span><span class="sxs-lookup"><span data-stu-id="3177e-262">The DC schema should use "unbounded".</span></span>|  
|`minOccurs`|<span data-ttu-id="3177e-263">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-263">Ignored.</span></span>|  
|`nillable`|<span data-ttu-id="3177e-264">Affecte le mappage de type.</span><span class="sxs-lookup"><span data-stu-id="3177e-264">Affects type mapping.</span></span> <span data-ttu-id="3177e-265">Cet attribut est ignoré pour les collections de dictionnaires.</span><span class="sxs-lookup"><span data-stu-id="3177e-265">This attribute is ignored for dictionary collections.</span></span>|  
  
### <a name="xselement-within-an-xsschema-global-element-declaration"></a><span data-ttu-id="3177e-266">\<xs : element > dans un \<xs : Schema > déclaration d’élément globale</span><span class="sxs-lookup"><span data-stu-id="3177e-266">\<xs:element> within an \<xs:schema> Global Element Declaration</span></span>  
  
- <span data-ttu-id="3177e-267">Une déclaration d'élément globale (GED) qui a les mêmes nom et espace de noms qu'un type dans le schéma, ou qui définit un type anonyme à l'intérieur d'elle-même, est considérée comme associée au type.</span><span class="sxs-lookup"><span data-stu-id="3177e-267">A Global Element Declaration (GED) that has the same name and namespace as a type in schema, or that defines an anonymous type inside itself, is said to be associated with the type.</span></span>  
  
- <span data-ttu-id="3177e-268">Exportation de schéma : les GED associées sont générées pour chaque type généré, simple et complexe.</span><span class="sxs-lookup"><span data-stu-id="3177e-268">Schema export: associated GEDs are generated for every generated type, both simple and complex.</span></span>  
  
- <span data-ttu-id="3177e-269">Désérialisation/sérialisation : les GED associées sont utilisées comme éléments racine pour le type.</span><span class="sxs-lookup"><span data-stu-id="3177e-269">Deserialization/serialization: associated GEDs are used as root elements for the type.</span></span>  
  
- <span data-ttu-id="3177e-270">Importation de schéma : les GED associées ne sont pas requises et sont ignorées si elles suivent les règles suivantes (à moins qu'elles définissent des types).</span><span class="sxs-lookup"><span data-stu-id="3177e-270">Schema import: associated GEDs are not required and are ignored if they follow the following rules (unless they define types).</span></span>  
  
|<span data-ttu-id="3177e-271">Attribut</span><span class="sxs-lookup"><span data-stu-id="3177e-271">Attribute</span></span>|<span data-ttu-id="3177e-272">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-272">Schema</span></span>|  
|---------------|------------|  
|`abstract`|<span data-ttu-id="3177e-273">Doit être faux pour les GED associées.</span><span class="sxs-lookup"><span data-stu-id="3177e-273">Must be false for associated GEDs.</span></span>|  
|`block`|<span data-ttu-id="3177e-274">Interdit dans les GED associées.</span><span class="sxs-lookup"><span data-stu-id="3177e-274">Forbidden in associated GEDs.</span></span>|  
|`default`|<span data-ttu-id="3177e-275">Interdit dans les GED associées.</span><span class="sxs-lookup"><span data-stu-id="3177e-275">Forbidden in associated GEDs.</span></span>|  
|`final`|<span data-ttu-id="3177e-276">Doit être faux pour les GED associées.</span><span class="sxs-lookup"><span data-stu-id="3177e-276">Must be false for associated GEDs.</span></span>|  
|`fixed`|<span data-ttu-id="3177e-277">Interdit dans les GED associées.</span><span class="sxs-lookup"><span data-stu-id="3177e-277">Forbidden in associated GEDs.</span></span>|  
|`id`|<span data-ttu-id="3177e-278">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-278">Ignored.</span></span>|  
|`name`|<span data-ttu-id="3177e-279">Prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-279">Supported.</span></span> <span data-ttu-id="3177e-280">Consultez la définition des GED associées.</span><span class="sxs-lookup"><span data-stu-id="3177e-280">See the definition of associated GEDs.</span></span>|  
|`nillable`|<span data-ttu-id="3177e-281">Doit être vrai pour les GED associées.</span><span class="sxs-lookup"><span data-stu-id="3177e-281">Must be true for associated GEDs.</span></span>|  
|`substitutionGroup`|<span data-ttu-id="3177e-282">Interdit dans les GED associées.</span><span class="sxs-lookup"><span data-stu-id="3177e-282">Forbidden in associated GEDs.</span></span>|  
|`type`|<span data-ttu-id="3177e-283">Pris en charge, doit correspondre au type associé pour les GED associées (à moins que l'élément contienne un type anonyme).</span><span class="sxs-lookup"><span data-stu-id="3177e-283">Supported, and must match the associated type for associated GEDs (unless the element contains an anonymous type).</span></span>|  
  
### <a name="xselement-contents"></a><span data-ttu-id="3177e-284">\<xs : element > : contenu</span><span class="sxs-lookup"><span data-stu-id="3177e-284">\<xs:element>: contents</span></span>  
  
|<span data-ttu-id="3177e-285">Sommaire</span><span class="sxs-lookup"><span data-stu-id="3177e-285">Contents</span></span>|<span data-ttu-id="3177e-286">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-286">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="3177e-287">Pris en charge.\*</span><span class="sxs-lookup"><span data-stu-id="3177e-287">Supported.\*</span></span>|  
|`complexType`|<span data-ttu-id="3177e-288">Pris en charge.\*</span><span class="sxs-lookup"><span data-stu-id="3177e-288">Supported.\*</span></span>|  
|`unique`|<span data-ttu-id="3177e-289">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-289">Ignored.</span></span>|  
|`key`|<span data-ttu-id="3177e-290">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-290">Ignored.</span></span>|  
|`keyref`|<span data-ttu-id="3177e-291">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-291">Ignored.</span></span>|  
|<span data-ttu-id="3177e-292">(vide)</span><span class="sxs-lookup"><span data-stu-id="3177e-292">(blank)</span></span>|<span data-ttu-id="3177e-293">Prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-293">Supported.</span></span>|  
  
 <span data-ttu-id="3177e-294">\* Lorsque vous utilisez le `simpleType` et `complexType,` mappage pour les types anonymes est le même que pour les types non anonymes, à ceci près qu’il n’existe aucun contrat de données anonymes, et donc un contrat de données nommé est créé, avec un nom généré dérivé du nom de l’élément.</span><span class="sxs-lookup"><span data-stu-id="3177e-294">\* When using the `simpleType` and `complexType,` mapping for anonymous types is the same as for non-anonymous types, except that there is no anonymous data contracts, and so a named data contract is created, with a generated name derived from the element name.</span></span> <span data-ttu-id="3177e-295">Les règles pour les types anonymes sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="3177e-295">The rules for anonymous types are in the following list:</span></span>  
  
- <span data-ttu-id="3177e-296">Détail d’implémentation de WCF : Si le `xs:element` nom ne contient pas de périodes, le type anonyme mappe à un type interne du type de contrat de données externe.</span><span class="sxs-lookup"><span data-stu-id="3177e-296">WCF implementation detail: If the `xs:element` name does not contain periods, the anonymous type maps to an inner type of the outer data contract type.</span></span> <span data-ttu-id="3177e-297">Si le nom contient des points, le type de contrat de données résultant est indépendant (n'est pas un type interne).</span><span class="sxs-lookup"><span data-stu-id="3177e-297">If the name contains periods, the resulting data contract type is independent (not an inner type).</span></span>  
  
- <span data-ttu-id="3177e-298">Le nom de contrat de données généré du type interne est le nom de contrat de données du type externe suivi par un point, le nom de l'élément et la chaîne "Type".</span><span class="sxs-lookup"><span data-stu-id="3177e-298">The generated data contract name of the inner type is the data contract name of the outer type followed by a period, the name of the element, and the string "Type".</span></span>  
  
- <span data-ttu-id="3177e-299">Si un contrat de données avec un tel nom existe déjà, le nom est rendu unique en ajoutant "1", "2", "3" et ainsi de suite jusqu'à ce qu'un nom unique soit créé.</span><span class="sxs-lookup"><span data-stu-id="3177e-299">If a data contract with such a name already exists, the name is made unique by appending "1", "2", "3", and so on until a unique name is created.</span></span>  
  
## <a name="simple-types---xssimpletype"></a><span data-ttu-id="3177e-300">Les Types simples - \<xs : simpleType ></span><span class="sxs-lookup"><span data-stu-id="3177e-300">Simple Types - \<xs:simpleType></span></span>  
  
### <a name="xssimpletype-attributes"></a><span data-ttu-id="3177e-301">\<xs : simpleType > : attributs</span><span class="sxs-lookup"><span data-stu-id="3177e-301">\<xs:simpleType>: attributes</span></span>  
  
|<span data-ttu-id="3177e-302">Attribut</span><span class="sxs-lookup"><span data-stu-id="3177e-302">Attribute</span></span>|<span data-ttu-id="3177e-303">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-303">Schema</span></span>|  
|---------------|------------|  
|`final`|<span data-ttu-id="3177e-304">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-304">Ignored.</span></span>|  
|`id`|<span data-ttu-id="3177e-305">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-305">Ignored.</span></span>|  
|`name`|<span data-ttu-id="3177e-306">Pris en charge, mappe au nom du contrat de données.</span><span class="sxs-lookup"><span data-stu-id="3177e-306">Supported, maps to the data contract name.</span></span>|  
  
### <a name="xssimpletype-contents"></a><span data-ttu-id="3177e-307">\<xs : simpleType > : contenu</span><span class="sxs-lookup"><span data-stu-id="3177e-307">\<xs:simpleType>: contents</span></span>  
  
|<span data-ttu-id="3177e-308">Sommaire</span><span class="sxs-lookup"><span data-stu-id="3177e-308">Contents</span></span>|<span data-ttu-id="3177e-309">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-309">Schema</span></span>|  
|--------------|------------|  
|`restriction`|<span data-ttu-id="3177e-310">Prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-310">Supported.</span></span> <span data-ttu-id="3177e-311">Mappe aux contrats de données d'énumération.</span><span class="sxs-lookup"><span data-stu-id="3177e-311">Maps to enumeration data contracts.</span></span> <span data-ttu-id="3177e-312">Cet attribut est ignoré s'il ne correspond pas au modèle d'énumération.</span><span class="sxs-lookup"><span data-stu-id="3177e-312">This attribute is ignored if it does not match the enumeration pattern.</span></span> <span data-ttu-id="3177e-313">Consultez la section des restrictions `xs:simpleType` .</span><span class="sxs-lookup"><span data-stu-id="3177e-313">See the `xs:simpleType` restrictions section.</span></span>|  
|`list`|<span data-ttu-id="3177e-314">Prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-314">Supported.</span></span> <span data-ttu-id="3177e-315">Mappe aux contrats de données d'énumération d'indicateur.</span><span class="sxs-lookup"><span data-stu-id="3177e-315">Maps to flag enumeration data contracts.</span></span> <span data-ttu-id="3177e-316">Consultez la section répertoriant `xs:simpleType` .</span><span class="sxs-lookup"><span data-stu-id="3177e-316">See the `xs:simpleType` lists section.</span></span>|  
|`union`|<span data-ttu-id="3177e-317">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-317">Forbidden.</span></span>|  
  
### <a name="xsrestriction"></a><span data-ttu-id="3177e-318">\<xs:restriction></span><span class="sxs-lookup"><span data-stu-id="3177e-318">\<xs:restriction></span></span>  
  
- <span data-ttu-id="3177e-319">Les restrictions de type complexe sont prises en charge uniquement pour la base = "`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="3177e-319">Complex type restrictions are supported only for base="`xs:anyType`".</span></span>  
  
- <span data-ttu-id="3177e-320">Les restrictions de type simple de `xs:string` qui n'ont pas de facettes de restriction autres que `xs:enumeration` sont mappées aux contrats de données d'énumération.</span><span class="sxs-lookup"><span data-stu-id="3177e-320">Simple type restrictions of `xs:string` that do not have any restriction facets other than `xs:enumeration` are mapped to enumeration data contracts.</span></span>  
  
- <span data-ttu-id="3177e-321">Toutes les autres restrictions de type simple sont mappées aux types qu'elles restreignent.</span><span class="sxs-lookup"><span data-stu-id="3177e-321">All other simple type restrictions are mapped to the types they restrict.</span></span> <span data-ttu-id="3177e-322">Par exemple, une restriction de `xs:int` mappe à un entier, tout comme `xs:int` lui-même.</span><span class="sxs-lookup"><span data-stu-id="3177e-322">For example, a restriction of `xs:int` maps to an integer, just as `xs:int` itself does.</span></span> <span data-ttu-id="3177e-323">Pour plus d’informations sur le mappage de type primitif, consultez le mappage de Type/primitif.</span><span class="sxs-lookup"><span data-stu-id="3177e-323">For more information about primitive type mapping, see Type/primitive mapping.</span></span>  
  
### <a name="xsrestriction-attributes"></a><span data-ttu-id="3177e-324">\<xs : restriction > : attributs</span><span class="sxs-lookup"><span data-stu-id="3177e-324">\<xs:restriction>: attributes</span></span>  
  
|<span data-ttu-id="3177e-325">Attribut</span><span class="sxs-lookup"><span data-stu-id="3177e-325">Attribute</span></span>|<span data-ttu-id="3177e-326">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-326">Schema</span></span>|  
|---------------|------------|  
|`base`|<span data-ttu-id="3177e-327">Doit être un type simple pris en charge ou `xs:anyType`.</span><span class="sxs-lookup"><span data-stu-id="3177e-327">Must be a supported simple type or `xs:anyType`.</span></span>|  
|`id`|<span data-ttu-id="3177e-328">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-328">Ignored.</span></span>|  
  
### <a name="xsrestriction-for-all-other-cases-contents"></a><span data-ttu-id="3177e-329">\<xs : restriction > pour tous les autres cas : contenu</span><span class="sxs-lookup"><span data-stu-id="3177e-329">\<xs:restriction> for all other cases: contents</span></span>  
  
|<span data-ttu-id="3177e-330">Sommaire</span><span class="sxs-lookup"><span data-stu-id="3177e-330">Contents</span></span>|<span data-ttu-id="3177e-331">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-331">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="3177e-332">Si présent, doit être dérivé d'un type primitif pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-332">If present, must be derived from a supported primitive type.</span></span>|  
|`minExclusive`|<span data-ttu-id="3177e-333">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-333">Ignored.</span></span>|  
|`minInclusive`|<span data-ttu-id="3177e-334">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-334">Ignored.</span></span>|  
|`maxExclusive`|<span data-ttu-id="3177e-335">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-335">Ignored.</span></span>|  
|`maxInclusive`|<span data-ttu-id="3177e-336">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-336">Ignored.</span></span>|  
|`totalDigits`|<span data-ttu-id="3177e-337">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-337">Ignored.</span></span>|  
|`fractionDigits`|<span data-ttu-id="3177e-338">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-338">Ignored.</span></span>|  
|`length`|<span data-ttu-id="3177e-339">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-339">Ignored.</span></span>|  
|`minLength`|<span data-ttu-id="3177e-340">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-340">Ignored.</span></span>|  
|`maxLength`|<span data-ttu-id="3177e-341">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-341">Ignored.</span></span>|  
|`enumeration`|<span data-ttu-id="3177e-342">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-342">Ignored.</span></span>|  
|`whiteSpace`|<span data-ttu-id="3177e-343">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-343">Ignored.</span></span>|  
|`pattern`|<span data-ttu-id="3177e-344">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-344">Ignored.</span></span>|  
|<span data-ttu-id="3177e-345">(vide)</span><span class="sxs-lookup"><span data-stu-id="3177e-345">(blank)</span></span>|<span data-ttu-id="3177e-346">Prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-346">Supported.</span></span>|  
  
## <a name="enumeration"></a><span data-ttu-id="3177e-347">Énumération</span><span class="sxs-lookup"><span data-stu-id="3177e-347">Enumeration</span></span>  
  
### <a name="xsrestriction-for-enumerations-attributes"></a><span data-ttu-id="3177e-348">\<xs : restriction > pour les énumérations : attributs</span><span class="sxs-lookup"><span data-stu-id="3177e-348">\<xs:restriction> for enumerations: attributes</span></span>  
  
|<span data-ttu-id="3177e-349">Attribut</span><span class="sxs-lookup"><span data-stu-id="3177e-349">Attribute</span></span>|<span data-ttu-id="3177e-350">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-350">Schema</span></span>|  
|---------------|------------|  
|`base`|<span data-ttu-id="3177e-351">Si présent, doit être `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="3177e-351">If present, must be `xs:string`.</span></span>|  
|`id`|<span data-ttu-id="3177e-352">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-352">Ignored.</span></span>|  
  
### <a name="xsrestriction-for-enumerations-contents"></a><span data-ttu-id="3177e-353">\<xs : restriction > pour les énumérations : contenu</span><span class="sxs-lookup"><span data-stu-id="3177e-353">\<xs:restriction> for enumerations: contents</span></span>  
  
|<span data-ttu-id="3177e-354">Sommaire</span><span class="sxs-lookup"><span data-stu-id="3177e-354">Contents</span></span>|<span data-ttu-id="3177e-355">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-355">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="3177e-356">Si présent, doit être une restriction d'énumération prise en charge par le contrat de données (cette section).</span><span class="sxs-lookup"><span data-stu-id="3177e-356">If present, must be an enumeration restriction supported by the data contract (this section).</span></span>|  
|`minExclusive`|<span data-ttu-id="3177e-357">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-357">Ignored.</span></span>|  
|`minInclusive`|<span data-ttu-id="3177e-358">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-358">Ignored.</span></span>|  
|`maxExclusive`|<span data-ttu-id="3177e-359">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-359">Ignored.</span></span>|  
|`maxInclusive`|<span data-ttu-id="3177e-360">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-360">Ignored.</span></span>|  
|`totalDigits`|<span data-ttu-id="3177e-361">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-361">Ignored.</span></span>|  
|`fractionDigits`|<span data-ttu-id="3177e-362">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-362">Ignored.</span></span>|  
|`length`|<span data-ttu-id="3177e-363">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-363">Forbidden.</span></span>|  
|`minLength`|<span data-ttu-id="3177e-364">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-364">Forbidden.</span></span>|  
|`maxLength`|<span data-ttu-id="3177e-365">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-365">Forbidden.</span></span>|  
|`enumeration`|<span data-ttu-id="3177e-366">Prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-366">Supported.</span></span> <span data-ttu-id="3177e-367">Le "id" d'énumération est ignoré, et "value" mappe au nom de la valeur dans le contrat de données d'énumération.</span><span class="sxs-lookup"><span data-stu-id="3177e-367">Enumeration "id" is ignored, and "value" maps to the value name in the enumeration data contract.</span></span>|  
|`whiteSpace`|<span data-ttu-id="3177e-368">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-368">Forbidden.</span></span>|  
|`pattern`|<span data-ttu-id="3177e-369">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-369">Forbidden.</span></span>|  
|<span data-ttu-id="3177e-370">(vide)</span><span class="sxs-lookup"><span data-stu-id="3177e-370">(empty)</span></span>|<span data-ttu-id="3177e-371">Pris en charge, mappe au type énumération vide.</span><span class="sxs-lookup"><span data-stu-id="3177e-371">Supported, maps to empty enumeration type.</span></span>|  
  
 <span data-ttu-id="3177e-372">Le code suivant montre une classe d'énumération C#.</span><span class="sxs-lookup"><span data-stu-id="3177e-372">The following code shows a C# enumeration class.</span></span>  
  
```csharp  
public enum MyEnum  
{  
  first = 3,  
  second = 4,  
  third =5  
}  
```  
  
 <span data-ttu-id="3177e-373">Cette classe mappe au schéma suivant par `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="3177e-373">This class maps to the following schema by the `DataContractSerializer`.</span></span> <span data-ttu-id="3177e-374">Si les valeurs d'énumération démarrent à partir de 1, les blocs `xs:annotation` ne sont pas générés.</span><span class="sxs-lookup"><span data-stu-id="3177e-374">If enumeration values start from 1, `xs:annotation` blocks are not generated.</span></span>  
  
```xml  
<xs:simpleType name="MyEnum">  
<xs:restriction base="xs:string">  
 <xs:enumeration value="first">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     3  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
 <xs:enumeration value="second">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     4  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
</xs:restriction>  
</xs:simpleType>  
```  
  
### <a name="xslist"></a><span data-ttu-id="3177e-375">\<xs:list></span><span class="sxs-lookup"><span data-stu-id="3177e-375">\<xs:list></span></span>  
 <span data-ttu-id="3177e-376">`DataContractSerializer` mappe des types énumération marqués avec `System.FlagsAttribute` à `xs:list` dérivé de `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="3177e-376">`DataContractSerializer` maps enumeration types marked with `System.FlagsAttribute` to `xs:list` derived from `xs:string`.</span></span> <span data-ttu-id="3177e-377">Aucune autre variation `xs:list` n'est prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-377">No other `xs:list` variations are supported.</span></span>  
  
### <a name="xslist-attributes"></a><span data-ttu-id="3177e-378">\<xs : List > : attributs</span><span class="sxs-lookup"><span data-stu-id="3177e-378">\<xs:list>: attributes</span></span>  
  
|<span data-ttu-id="3177e-379">Attribut</span><span class="sxs-lookup"><span data-stu-id="3177e-379">Attribute</span></span>|<span data-ttu-id="3177e-380">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-380">Schema</span></span>|  
|---------------|------------|  
|`itemType`|<span data-ttu-id="3177e-381">Interdit.</span><span class="sxs-lookup"><span data-stu-id="3177e-381">Forbidden.</span></span>|  
|`id`|<span data-ttu-id="3177e-382">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-382">Ignored.</span></span>|  
  
### <a name="xslist-contents"></a><span data-ttu-id="3177e-383">\<xs : List > : contenu</span><span class="sxs-lookup"><span data-stu-id="3177e-383">\<xs:list>: contents</span></span>  
  
|<span data-ttu-id="3177e-384">Sommaire</span><span class="sxs-lookup"><span data-stu-id="3177e-384">Contents</span></span>|<span data-ttu-id="3177e-385">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-385">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="3177e-386">Doit être une restriction de `xs:string` utilisant la facette `xs:enumeration` .</span><span class="sxs-lookup"><span data-stu-id="3177e-386">Must be restriction from `xs:string` using `xs:enumeration` facet.</span></span>|  
  
 <span data-ttu-id="3177e-387">Si la valeur d'énumération ne suit pas une progression de puissance de 2 (valeur par défaut pour les indicateurs), la valeur est stockée dans l'élément `xs:annotation/xs:appInfo/ser:EnumerationValue` .</span><span class="sxs-lookup"><span data-stu-id="3177e-387">If enumeration value does not follow a power of 2 progression (default for Flags), the value is stored in the `xs:annotation/xs:appInfo/ser:EnumerationValue` element.</span></span>  
  
 <span data-ttu-id="3177e-388">Par exemple, le code suivant marque un type énumération.</span><span class="sxs-lookup"><span data-stu-id="3177e-388">For example, the following code flags an enumeration type.</span></span>  
  
```csharp  
[Flags]  
public enum AuthFlags  
{    
  AuthAnonymous = 1,  
  AuthBasic = 2,  
  AuthNTLM = 4,  
  AuthMD5 = 16,  
  AuthWindowsLiveID = 64,  
}  
```  
  
 <span data-ttu-id="3177e-389">Ce type mappe au schéma suivant.</span><span class="sxs-lookup"><span data-stu-id="3177e-389">This type maps to the following schema.</span></span>  
  
```xml  
<xs:simpleType name="AuthFlags">  
    <xs:list>  
      <xs:simpleType>  
        <xs:restriction base="xs:string">  
          <xs:enumeration value="AuthAnonymous" />  
          <xs:enumeration value="AuthBasic" />  
          <xs:enumeration value="AuthNTLM" />  
          <xs:enumeration value="AuthMD5">  
            <xs:annotation>  
              <xs:appinfo>  
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">16</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
          <xs:enumeration value="AuthWindowsLiveID">  
            <xs:annotation>  
              <xs:appinfo>  
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">64</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:list>  
  </xs:simpleType>  
```  
  
## <a name="inheritance"></a><span data-ttu-id="3177e-390">Héritage</span><span class="sxs-lookup"><span data-stu-id="3177e-390">Inheritance</span></span>  
  
### <a name="general-rules"></a><span data-ttu-id="3177e-391">Règles Générales</span><span class="sxs-lookup"><span data-stu-id="3177e-391">General rules</span></span>  
 <span data-ttu-id="3177e-392">Un contrat de données peut hériter d'un autre contrat de données.</span><span class="sxs-lookup"><span data-stu-id="3177e-392">A data contract can inherit from another data contract.</span></span> <span data-ttu-id="3177e-393">De tels contrats de données mappent à une base et sont dérivés des types d'extension à l'aide de la construction de schéma XML `<xs:extension>` .</span><span class="sxs-lookup"><span data-stu-id="3177e-393">Such data contracts map to a base and are derived by extension types using the `<xs:extension>` XML Schema construct.</span></span>  
  
 <span data-ttu-id="3177e-394">Un contrat de données ne peut pas hériter d'un contrat de données de collection.</span><span class="sxs-lookup"><span data-stu-id="3177e-394">A data contract cannot inherit from a collection data contract.</span></span>  
  
 <span data-ttu-id="3177e-395">Le code ci-dessous montre un exemple de contrat de données.</span><span class="sxs-lookup"><span data-stu-id="3177e-395">For example, the following code is a data contract.</span></span>  
  
```csharp  
[DataContract]  
public class Person  
{  
  [DataMember]  
  public string Name;  
}  
[DataContract]  
public class Employee : Person   
{      
  [DataMember]  
  public int ID;  
}  
```  
  
 <span data-ttu-id="3177e-396">Ce contrat de données mappe à la déclaration de type de schéma XML suivante.</span><span class="sxs-lookup"><span data-stu-id="3177e-396">This data contract maps to the following XML Schema type declaration.</span></span>  
  
```xml  
<xs:complexType name="Employee">  
 <xs:complexContent mixed="false">  
  <xs:extension base="tns:Person">  
   <xs:sequence>  
    <xs:element minOccurs="0" name="ID" type="xs:int"/>  
   </xs:sequence>  
  </xs:extension>  
 </xs:complexContent>  
</xs:complexType>  
<xs:complexType name="Person">  
 <xs:sequence>  
  <xs:element minOccurs="0" name="Name"   
    nillable="true" type="xs:string"/>  
 </xs:sequence>  
</xs:complexType>  
```  
  
### <a name="xscomplexcontent-attributes"></a><span data-ttu-id="3177e-397">\<xs : complexContent > : attributs</span><span class="sxs-lookup"><span data-stu-id="3177e-397">\<xs:complexContent>: attributes</span></span>  
  
|<span data-ttu-id="3177e-398">Attribut</span><span class="sxs-lookup"><span data-stu-id="3177e-398">Attribute</span></span>|<span data-ttu-id="3177e-399">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-399">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="3177e-400">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-400">Ignored.</span></span>|  
|`mixed`|<span data-ttu-id="3177e-401">Doit être faux.</span><span class="sxs-lookup"><span data-stu-id="3177e-401">Must be false.</span></span>|  
  
### <a name="xscomplexcontent-contents"></a><span data-ttu-id="3177e-402">\<xs : complexContent > : contenu</span><span class="sxs-lookup"><span data-stu-id="3177e-402">\<xs:complexContent>: contents</span></span>  
  
|<span data-ttu-id="3177e-403">Sommaire</span><span class="sxs-lookup"><span data-stu-id="3177e-403">Contents</span></span>|<span data-ttu-id="3177e-404">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-404">Schema</span></span>|  
|--------------|------------|  
|`restriction`|<span data-ttu-id="3177e-405">Interdit, sauf lorsque la base = "`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="3177e-405">Forbidden, except when base="`xs:anyType`".</span></span> <span data-ttu-id="3177e-406">Ce qui précède équivaut à placer directement le contenu de `xs:restriction` sous le conteneur de `xs:complexContent`.</span><span class="sxs-lookup"><span data-stu-id="3177e-406">The latter is equivalent to placing the content of the `xs:restriction` directly under the container of the `xs:complexContent`.</span></span>|  
|`extension`|<span data-ttu-id="3177e-407">Prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-407">Supported.</span></span> <span data-ttu-id="3177e-408">Mappe à l'héritage de contrat de données.</span><span class="sxs-lookup"><span data-stu-id="3177e-408">Maps to data contract inheritance.</span></span>|  
  
### <a name="xsextension-in-xscomplexcontent-attributes"></a><span data-ttu-id="3177e-409">\<xs : extension > dans \<xs : complexContent > : attributs</span><span class="sxs-lookup"><span data-stu-id="3177e-409">\<xs:extension> in \<xs:complexContent>: attributes</span></span>  
  
|<span data-ttu-id="3177e-410">Attribut</span><span class="sxs-lookup"><span data-stu-id="3177e-410">Attribute</span></span>|<span data-ttu-id="3177e-411">Schéma</span><span class="sxs-lookup"><span data-stu-id="3177e-411">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="3177e-412">Ignoré.</span><span class="sxs-lookup"><span data-stu-id="3177e-412">Ignored.</span></span>|  
|`base`|<span data-ttu-id="3177e-413">Prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3177e-413">Supported.</span></span> <span data-ttu-id="3177e-414">Mappe au type de contrat de données de base de qui ce type hérite.</span><span class="sxs-lookup"><span data-stu-id="3177e-414">Maps to the base data contract type that this type inherits from.</span></span>|  
  
### <a name="xsextension-in-xscomplexcontent-contents"></a><span data-ttu-id="3177e-415">\<xs : extension > dans \<xs : complexContent > : contenu</span><span class="sxs-lookup"><span data-stu-id="3177e-415">\<xs:extension> in \<xs:complexContent>: contents</span></span>  
 <span data-ttu-id="3177e-416">Les règles sont les mêmes que pour le contenu `<xs:complexType>` .</span><span class="sxs-lookup"><span data-stu-id="3177e-416">The rules are the same as for `<xs:complexType>` contents.</span></span>  
  
 <span data-ttu-id="3177e-417">Si un `<xs:sequence>` est fourni, ses éléments membres mappent aux membres de données supplémentaires qui sont présents dans le contrat de données dérivé.</span><span class="sxs-lookup"><span data-stu-id="3177e-417">If an `<xs:sequence>` is provided, its member elements map to additional data members that are present in the derived data contract.</span></span>  
  
 <span data-ttu-id="3177e-418">Si un type dérivé contient un élément portant le même nom qu'un élément dans un type de base, la déclaration d'élément en double mappe à un membre de données avec un nom généré pour être unique.</span><span class="sxs-lookup"><span data-stu-id="3177e-418">If a derived type contains an element with the same name as an element in a base type, the duplicate element declaration maps to a data member with a name that is generated to be unique.</span></span> <span data-ttu-id="3177e-419">Des entiers positifs sont ajoutés au nom du membre de données ("member1", "member2" et ainsi de suite) jusqu'à ce qu'un nom unique soit trouvé.</span><span class="sxs-lookup"><span data-stu-id="3177e-419">Positive integer numbers are added to the data member name ("member1", "member2", and so on) until a unique name is found.</span></span> <span data-ttu-id="3177e-420">Inversement :</span><span class="sxs-lookup"><span data-stu-id="3177e-420">Conversely:</span></span>  
  
- <span data-ttu-id="3177e-421">Si un contrat de données dérivé a un membre de données portant le même nom et type qu'un membre de données dans un contrat de données de base, `DataContractSerializer` génère cet élément correspondant dans le type dérivé.</span><span class="sxs-lookup"><span data-stu-id="3177e-421">If a derived data contract has a data member with the same name and type as a data member in a base data contract, `DataContractSerializer` generates this corresponding element in the derived type.</span></span>  
  
- <span data-ttu-id="3177e-422">Si un contrat de données dérivé a un membre de données portant le même nom qu'un membre de données dans un contrat de données de base mais ayant un type différent, `DataContractSerializer` importe un schéma avec un élément de type `xs:anyType` à la fois dans le type de base et dans les déclarations de type dérivé.</span><span class="sxs-lookup"><span data-stu-id="3177e-422">If a derived data contract has a data member with the same name as a data member in a base data contract but a different type, the `DataContractSerializer` imports a schema with an element of the type `xs:anyType` in both base type and derived type declarations.</span></span> <span data-ttu-id="3177e-423">Le nom du type d'origine est conservé dans `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span><span class="sxs-lookup"><span data-stu-id="3177e-423">The original type name is preserved in `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span></span>  
  
 <span data-ttu-id="3177e-424">Les deux variations peuvent aboutir à schéma ayant un modèle de contenu ambigu, qui dépend de l'ordre des membres de données respectifs.</span><span class="sxs-lookup"><span data-stu-id="3177e-424">Both variations may lead to a schema with an ambiguous content model, which depends on the order of the respective data members.</span></span>  
  
## <a name="typeprimitive-mapping"></a><span data-ttu-id="3177e-425">Mappage de type/primitif</span><span class="sxs-lookup"><span data-stu-id="3177e-425">Type/primitive mapping</span></span>  
 <span data-ttu-id="3177e-426">`DataContractSerializer` utilise le mappage suivant pour les types primitifs de schéma XML.</span><span class="sxs-lookup"><span data-stu-id="3177e-426">The `DataContractSerializer` uses the following mapping for XML Schema primitive types.</span></span>  
  
|<span data-ttu-id="3177e-427">Type XSD</span><span class="sxs-lookup"><span data-stu-id="3177e-427">XSD type</span></span>|<span data-ttu-id="3177e-428">Type .NET</span><span class="sxs-lookup"><span data-stu-id="3177e-428">.NET type</span></span>|  
|--------------|---------------|  
|`anyType`|<span data-ttu-id="3177e-429"><xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="3177e-429"><xref:System.Object>.</span></span>|  
|`anySimpleType`|<span data-ttu-id="3177e-430"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-430"><xref:System.String>.</span></span>|  
|`duration`|<span data-ttu-id="3177e-431"><xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="3177e-431"><xref:System.TimeSpan>.</span></span>|  
|`dateTime`|<span data-ttu-id="3177e-432"><xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="3177e-432"><xref:System.DateTime>.</span></span>|  
|`dateTimeOffset`|<span data-ttu-id="3177e-433">Objets<xref:System.DateTime> et <xref:System.TimeSpan> pour l'offset.</span><span class="sxs-lookup"><span data-stu-id="3177e-433"><xref:System.DateTime> and <xref:System.TimeSpan> for the offset.</span></span> <span data-ttu-id="3177e-434">Consultez Sérialisation DateTimeOffset ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="3177e-434">See DateTimeOffset Serialization below.</span></span>|  
|`time`|<span data-ttu-id="3177e-435"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-435"><xref:System.String>.</span></span>|  
|`date`|<span data-ttu-id="3177e-436"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-436"><xref:System.String>.</span></span>|  
|`gYearMonth`|<span data-ttu-id="3177e-437"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-437"><xref:System.String>.</span></span>|  
|`gYear`|<span data-ttu-id="3177e-438"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-438"><xref:System.String>.</span></span>|  
|`gMonthDay`|<span data-ttu-id="3177e-439"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-439"><xref:System.String>.</span></span>|  
|`gDay`|<span data-ttu-id="3177e-440"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-440"><xref:System.String>.</span></span>|  
|`gMonth`|<span data-ttu-id="3177e-441"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-441"><xref:System.String>.</span></span>|  
|`boolean`|<xref:System.Boolean>|  
|`base64Binary`|<span data-ttu-id="3177e-442">Tableau<xref:System.Byte> .</span><span class="sxs-lookup"><span data-stu-id="3177e-442"><xref:System.Byte> array.</span></span>|  
|`hexBinary`|<span data-ttu-id="3177e-443"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-443"><xref:System.String>.</span></span>|  
|`float`|<span data-ttu-id="3177e-444"><xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="3177e-444"><xref:System.Single>.</span></span>|  
|`double`|<span data-ttu-id="3177e-445"><xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="3177e-445"><xref:System.Double>.</span></span>|  
|`anyURI`|<span data-ttu-id="3177e-446"><xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="3177e-446"><xref:System.Uri>.</span></span>|  
|`QName`|<span data-ttu-id="3177e-447"><xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="3177e-447"><xref:System.Xml.XmlQualifiedName>.</span></span>|  
|`string`|<span data-ttu-id="3177e-448"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-448"><xref:System.String>.</span></span>|  
|`normalizedString`|<span data-ttu-id="3177e-449"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-449"><xref:System.String>.</span></span>|  
|`token`|<span data-ttu-id="3177e-450"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-450"><xref:System.String>.</span></span>|  
|`language`|<span data-ttu-id="3177e-451"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-451"><xref:System.String>.</span></span>|  
|`Name`|<span data-ttu-id="3177e-452"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-452"><xref:System.String>.</span></span>|  
|`NCName`|<span data-ttu-id="3177e-453"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-453"><xref:System.String>.</span></span>|  
|`ID`|<span data-ttu-id="3177e-454"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-454"><xref:System.String>.</span></span>|  
|`IDREF`|<span data-ttu-id="3177e-455"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-455"><xref:System.String>.</span></span>|  
|`IDREFS`|<span data-ttu-id="3177e-456"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-456"><xref:System.String>.</span></span>|  
|`ENTITY`|<span data-ttu-id="3177e-457"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-457"><xref:System.String>.</span></span>|  
|`ENTITIES`|<span data-ttu-id="3177e-458"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-458"><xref:System.String>.</span></span>|  
|`NMTOKEN`|<span data-ttu-id="3177e-459"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-459"><xref:System.String>.</span></span>|  
|`NMTOKENS`|<span data-ttu-id="3177e-460"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3177e-460"><xref:System.String>.</span></span>|  
|`decimal`|<span data-ttu-id="3177e-461"><xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="3177e-461"><xref:System.Decimal>.</span></span>|  
|`integer`|<span data-ttu-id="3177e-462"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="3177e-462"><xref:System.Int64>.</span></span>|  
|`nonPositiveInteger`|<span data-ttu-id="3177e-463"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="3177e-463"><xref:System.Int64>.</span></span>|  
|`negativeInteger`|<span data-ttu-id="3177e-464"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="3177e-464"><xref:System.Int64>.</span></span>|  
|`long`|<span data-ttu-id="3177e-465"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="3177e-465"><xref:System.Int64>.</span></span>|  
|`int`|<span data-ttu-id="3177e-466"><xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="3177e-466"><xref:System.Int32>.</span></span>|  
|`short`|<span data-ttu-id="3177e-467"><xref:System.Int16>.</span><span class="sxs-lookup"><span data-stu-id="3177e-467"><xref:System.Int16>.</span></span>|  
|`Byte`|<span data-ttu-id="3177e-468"><xref:System.SByte>.</span><span class="sxs-lookup"><span data-stu-id="3177e-468"><xref:System.SByte>.</span></span>|  
|`nonNegativeInteger`|<span data-ttu-id="3177e-469"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="3177e-469"><xref:System.Int64>.</span></span>|  
|`unsignedLong`|<span data-ttu-id="3177e-470"><xref:System.UInt64>.</span><span class="sxs-lookup"><span data-stu-id="3177e-470"><xref:System.UInt64>.</span></span>|  
|`unsignedInt`|<span data-ttu-id="3177e-471"><xref:System.UInt32>.</span><span class="sxs-lookup"><span data-stu-id="3177e-471"><xref:System.UInt32>.</span></span>|  
|`unsignedShort`|<span data-ttu-id="3177e-472"><xref:System.UInt16>.</span><span class="sxs-lookup"><span data-stu-id="3177e-472"><xref:System.UInt16>.</span></span>|  
|`unsignedByte`|<span data-ttu-id="3177e-473"><xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="3177e-473"><xref:System.Byte>.</span></span>|  
|`positiveInteger`|<span data-ttu-id="3177e-474"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="3177e-474"><xref:System.Int64>.</span></span>|  
  
## <a name="iserializable-types-mapping"></a><span data-ttu-id="3177e-475">Mappage de types ISerializable</span><span class="sxs-lookup"><span data-stu-id="3177e-475">ISerializable types mapping</span></span>  
 <span data-ttu-id="3177e-476">Dans le [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.0, <xref:System.Runtime.Serialization.ISerializable> a été introduit comme mécanisme général pour sérialiser des objets pour la persistance ou le transfert de données.</span><span class="sxs-lookup"><span data-stu-id="3177e-476">In [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.0, <xref:System.Runtime.Serialization.ISerializable> was introduced as a general mechanism to serialize objects for persistence or data transfer.</span></span> <span data-ttu-id="3177e-477">Il existe de nombreux types [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] qui implémentent `ISerializable` et qui peuvent être passés entre les applications.</span><span class="sxs-lookup"><span data-stu-id="3177e-477">There are many [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types that implement `ISerializable` and that can be passed between applications.</span></span> <span data-ttu-id="3177e-478"><xref:System.Runtime.Serialization.DataContractSerializer> fournit naturellement le support pour les classes `ISerializable` .</span><span class="sxs-lookup"><span data-stu-id="3177e-478"><xref:System.Runtime.Serialization.DataContractSerializer> naturally provides support for `ISerializable` classes.</span></span> <span data-ttu-id="3177e-479">`DataContractSerializer` mappe des types de schéma d'implémentation `ISerializable` qui diffèrent uniquement par le QName (nom qualifié) du type et sont des collections de propriétés.</span><span class="sxs-lookup"><span data-stu-id="3177e-479">The `DataContractSerializer` maps `ISerializable` implementation schema types that differ only by the QName (qualified name) of the type and are effectively property collections.</span></span> <span data-ttu-id="3177e-480">Par exemple, le `DataContractSerializer` mappe <xref:System.Exception> au type XSD suivant dans le `http://schemas.datacontract.org/2004/07/System` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="3177e-480">For example, the `DataContractSerializer` maps <xref:System.Exception> to the following XSD type in the `http://schemas.datacontract.org/2004/07/System` namespace.</span></span>  
  
```xml  
<xs:complexType name="Exception">  
 <xs:sequence>  
  <xs:any minOccurs="0" maxOccurs="unbounded"   
      namespace="##local" processContents="skip"/>  
 </xs:sequence>  
 <xs:attribute ref="ser:FactoryType"/>  
</xs:complexType>  
```  
  
 <span data-ttu-id="3177e-481">L'attribut facultatif `ser:FactoryType` déclaré dans le schéma de sérialisation du contrat de données référence une classe de fabrique qui peut désérialiser le type.</span><span class="sxs-lookup"><span data-stu-id="3177e-481">The optional attribute `ser:FactoryType` declared in the Data Contract Serialization schema references a factory class that can deserialize the type.</span></span> <span data-ttu-id="3177e-482">La classe de fabrique doit faire partie de la collection de types connus de l'instance `DataContractSerializer` qui est utilisée.</span><span class="sxs-lookup"><span data-stu-id="3177e-482">The factory class must be part of the known types collection of the `DataContractSerializer` instance being used.</span></span> <span data-ttu-id="3177e-483">Pour plus d’informations sur les types connus, consultez [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="3177e-483">For more information about known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="datacontract-serialization-schema"></a><span data-ttu-id="3177e-484">Schéma de sérialisation DataContract</span><span class="sxs-lookup"><span data-stu-id="3177e-484">DataContract Serialization Schema</span></span>  
 <span data-ttu-id="3177e-485">Plusieurs schémas exportés par `DataContractSerializer` , utilisent des types, des éléments et des attributs d'un espace de noms spécial de la sérialisation du contrat de données :</span><span class="sxs-lookup"><span data-stu-id="3177e-485">A number of schemas exported by the `DataContractSerializer` use types, elements, and attributes from a special Data Contract Serialization namespace:</span></span>  
  
 `http://schemas.microsoft.com/2003/10/Serialization`
  
 <span data-ttu-id="3177e-486">Voici une déclaration de schéma de sérialisation du contrat de données complète.</span><span class="sxs-lookup"><span data-stu-id="3177e-486">The following is a complete Data Contract Serialization schema declaration.</span></span>  
  
```xml  
<xs:schema attributeFormDefault="qualified"          
   elementFormDefault="qualified"        
   targetNamespace =   
    "http://schemas.microsoft.com/2003/10/Serialization/"   
   xmlns:xs="http://www.w3.org/2001/XMLSchema"        
   xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/">  
  
 <!-- Top-level elements for primitive types. -->  
 <xs:element name="anyType" nillable="true" type="xs:anyType"/>  
 <xs:element name="anyURI" nillable="true" type="xs:anyURI"/>  
 <xs:element name="base64Binary"  
       nillable="true" type="xs:base64Binary"/>  
 <xs:element name="boolean" nillable="true" type="xs:boolean"/>  
 <xs:element name="byte" nillable="true" type="xs:byte"/>  
 <xs:element name="dateTime" nillable="true" type="xs:dateTime"/>  
 <xs:element name="decimal" nillable="true" type="xs:decimal"/>  
 <xs:element name="double" nillable="true" type="xs:double"/>  
 <xs:element name="float" nillable="true" type="xs:float"/>  
 <xs:element name="int" nillable="true" type="xs:int"/>  
 <xs:element name="long" nillable="true" type="xs:long"/>  
 <xs:element name="QName" nillable="true" type="xs:QName"/>  
 <xs:element name="short" nillable="true" type="xs:short"/>  
 <xs:element name="string" nillable="true" type="xs:string"/>  
 <xs:element name="unsignedByte"  
       nillable="true" type="xs:unsignedByte"/>  
 <xs:element name="unsignedInt"  
       nillable="true" type="xs:unsignedInt"/>  
 <xs:element name="unsignedLong"  
       nillable="true" type="xs:unsignedLong"/>  
 <xs:element name="unsignedShort"  
       nillable="true" type="xs:unsignedShort"/>  
  
 <!-- Primitive types introduced for certain .NET simple types. -->  
 <xs:element name="char" nillable="true" type="tns:char"/>  
 <xs:simpleType name="char">  
  <xs:restriction base="xs:int"/>  
 </xs:simpleType>  
  
 <!-- xs:duration is restricted to an ordered value space,  
    to map to System.TimeSpan -->  
 <xs:element name="duration" nillable="true" type="tns:duration"/>  
 <xs:simpleType name="duration">  
  <xs:restriction base="xs:duration">  
   <xs:pattern   
     value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?"/>  
   <xs:minInclusive value="-P10675199DT2H48M5.4775808S"/>  
   <xs:maxInclusive value="P10675199DT2H48M5.4775807S"/>  
  </xs:restriction>  
 </xs:simpleType>  
  
 <xs:element name="guid" nillable="true" type="tns:guid"/>  
 <xs:simpleType name="guid">  
  <xs:restriction base="xs:string">  
   <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}"/>  
  </xs:restriction>  
 </xs:simpleType>  
  
 <!-- This is used for schemas exported from ISerializable type. -->  
 <xs:attribute name="FactoryType" type="xs:QName"/>  
</xs:schema>  
```  
  
 <span data-ttu-id="3177e-487">Il convient de remarquer les points suivants :</span><span class="sxs-lookup"><span data-stu-id="3177e-487">The following should be noted:</span></span>  
  
- <span data-ttu-id="3177e-488">`ser:char` est introduit pour représenter des caractères Unicode de type <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="3177e-488">`ser:char` is introduced to represent Unicode characters of type <xref:System.Char>.</span></span>  
  
- <span data-ttu-id="3177e-489">Le `valuespace` de `xs:duration` est réduit à un jeu ordonné afin qu'il puisse être mappé à un <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="3177e-489">The `valuespace` of `xs:duration` is reduced to an ordered set so that it can be mapped to a <xref:System.TimeSpan>.</span></span>  
  
- <span data-ttu-id="3177e-490">`FactoryType` est utilisé dans les schémas exportés des types dérivés de <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="3177e-490">`FactoryType` is used in schemas exported from types that are derived from <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
## <a name="importing-non-datacontract-schemas"></a><span data-ttu-id="3177e-491">Importation de schémas qui ne sont pas DataContract</span><span class="sxs-lookup"><span data-stu-id="3177e-491">Importing non-DataContract schemas</span></span>  
 <span data-ttu-id="3177e-492">`DataContractSerializer` dispose de l'option `ImportXmlTypes` pour autoriser l'importation des schémas non conformes au profil XSD `DataContractSerializer` (consultez la propriété <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> ).</span><span class="sxs-lookup"><span data-stu-id="3177e-492">`DataContractSerializer` has the `ImportXmlTypes` option to allow import of schemas that do not conform to the `DataContractSerializer` XSD profile (see the <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> property).</span></span> <span data-ttu-id="3177e-493">Affecter à cette option la valeur `true` active l'acceptation des types de schémas non conformes et les mappe à l'implémentation suivante, <xref:System.Xml.Serialization.IXmlSerializable> qui encapsule un tableau de <xref:System.Xml.XmlNode> (seul le nom de la classe diffère).</span><span class="sxs-lookup"><span data-stu-id="3177e-493">Setting this option to `true` enables acceptance of non-conforming schema types and mapping them to the following implementation, <xref:System.Xml.Serialization.IXmlSerializable> wrapping an array of <xref:System.Xml.XmlNode> (only the class name differs).</span></span>  
  
```csharp  
[GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
[System.Xml.Serialization.XmlSchemaProviderAttribute("ExportSchema")]  
[System.Xml.Serialization.XmlRootAttribute(IsNullable=false)]  
public partial class Person : object, IXmlSerializable  
{    
  private XmlNode[] nodesField;    
  private static XmlQualifiedName typeName =   
new XmlQualifiedName("Person","http://Microsoft.ServiceModel.Samples");    
  public XmlNode[] Nodes  
  {  
    get {return this.nodesField;}  
    set {this.nodesField = value;}  
  }    
  public void ReadXml(XmlReader reader)  
  {  
    this.nodesField = XmlSerializableServices.ReadNodes(reader);  
  }    
  public void WriteXml(XmlWriter writer)  
  {  
    XmlSerializableServices.WriteNodes(writer, this.Nodes);  
  }    
  public System.Xml.Schema.XmlSchema GetSchema()  
  {  
    return null;  
  }    
  public static XmlQualifiedName ExportSchema(XmlSchemaSet schemas)  
  {  
    XmlSerializableServices.AddDefaultSchema(schemas, typeName);  
    return typeName;  
  }  
}  
```  
  
## <a name="datetimeoffset-serialization"></a><span data-ttu-id="3177e-494">Sérialisation DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="3177e-494">DateTimeOffset Serialization</span></span>  
 <span data-ttu-id="3177e-495"><xref:System.DateTimeOffset> n'est pas traité comme un type primitif.</span><span class="sxs-lookup"><span data-stu-id="3177e-495">The <xref:System.DateTimeOffset> is not treated as a primitive type.</span></span> <span data-ttu-id="3177e-496">À la place, il est sérialisé comme un élément complexe comportant deux parties.</span><span class="sxs-lookup"><span data-stu-id="3177e-496">Instead, it is serialized as a complex element with two parts.</span></span> <span data-ttu-id="3177e-497">La première partie représente la date et l'heure et la deuxième partie représente l'offset de la date et de l'heure.</span><span class="sxs-lookup"><span data-stu-id="3177e-497">The first part represents the date time, and the second part represents the offset from the date time.</span></span> <span data-ttu-id="3177e-498">Un exemple d'une valeur DateTimeOffset sérialisée est illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="3177e-498">An example of a serialized DateTimeOffset value is shown in the following code.</span></span>  
  
```xml  
<OffSet xmlns:a="http://schemas.datacontract.org/2004/07/System">  
  <DateTime i:type="b:dateTime" xmlns=""   
    xmlns:b="http://www.w3.org/2001/XMLSchema">2008-08-28T08:00:00    
  </DateTime>   
  <OffsetMinutes i:type="b:short" xmlns=""   
   xmlns:b="http://www.w3.org/2001/XMLSchema">-480  
   </OffsetMinutes>   
</OffSet>  
```  
  
 <span data-ttu-id="3177e-499">Le schéma se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="3177e-499">The schema is as follows.</span></span>  
  
```xml  
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">  
   <xs:complexType name="DateTimeOffset">  
      <xs:sequence minOccurs="1" maxOccurs="1">  
         <xs:element name="DateTime" type="xs:dateTime"  
         minOccurs="1" maxOccurs="1" />  
         <xs:element name="OffsetMinutes" type="xs:short"  
         minOccurs="1" maxOccurs="1" />  
      </xs:sequence>  
   </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3177e-500">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3177e-500">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- [<span data-ttu-id="3177e-501">Utilisation de contrats de données</span><span class="sxs-lookup"><span data-stu-id="3177e-501">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
