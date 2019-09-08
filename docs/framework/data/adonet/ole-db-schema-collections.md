---
title: Collections de schémas OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 2d5718c12100ebea49a6b6fab29a3790918c6ad3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783451"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="65f6e-102">Collections de schémas OLE DB</span><span class="sxs-lookup"><span data-stu-id="65f6e-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="65f6e-103">Cette section traite de la prise en charge des collections de schémas pour les fournisseurs OLE DB de Microsoft SQL Server, Oracle et Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="65f6e-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="65f6e-104">Fournisseur Microsoft SQL Server OLE DB</span><span class="sxs-lookup"><span data-stu-id="65f6e-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="65f6e-105">Le pilote Microsoft SQL Server OLE DB prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="65f6e-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="65f6e-106">Tables</span><span class="sxs-lookup"><span data-stu-id="65f6e-106">Tables</span></span>  
  
- <span data-ttu-id="65f6e-107">Colonnes</span><span class="sxs-lookup"><span data-stu-id="65f6e-107">Columns</span></span>  
  
- <span data-ttu-id="65f6e-108">Procédures</span><span class="sxs-lookup"><span data-stu-id="65f6e-108">Procedures</span></span>  
  
- <span data-ttu-id="65f6e-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="65f6e-109">ProcedureParameters</span></span>  
  
- <span data-ttu-id="65f6e-110">Catalogue</span><span class="sxs-lookup"><span data-stu-id="65f6e-110">Catalog</span></span>  
  
- <span data-ttu-id="65f6e-111">Index</span><span class="sxs-lookup"><span data-stu-id="65f6e-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="65f6e-112">Tables</span><span class="sxs-lookup"><span data-stu-id="65f6e-112">Tables</span></span>  
  
|<span data-ttu-id="65f6e-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="65f6e-113">ColumnName</span></span>|<span data-ttu-id="65f6e-114">Type de données</span><span class="sxs-lookup"><span data-stu-id="65f6e-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="65f6e-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-115">TABLE_CATALOG</span></span>|<span data-ttu-id="65f6e-116">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-116">String</span></span>|  
|<span data-ttu-id="65f6e-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="65f6e-118">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-118">String</span></span>|  
|<span data-ttu-id="65f6e-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-119">TABLE_NAME</span></span>|<span data-ttu-id="65f6e-120">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-120">String</span></span>|  
|<span data-ttu-id="65f6e-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="65f6e-121">TABLE_TYPE</span></span>|<span data-ttu-id="65f6e-122">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-122">String</span></span>|  
|<span data-ttu-id="65f6e-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="65f6e-123">TABLE_GUID</span></span>|<span data-ttu-id="65f6e-124">Guid</span><span class="sxs-lookup"><span data-stu-id="65f6e-124">Guid</span></span>|  
|<span data-ttu-id="65f6e-125">Description</span><span class="sxs-lookup"><span data-stu-id="65f6e-125">DESCRIPTION</span></span>|<span data-ttu-id="65f6e-126">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-126">String</span></span>|  
|<span data-ttu-id="65f6e-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="65f6e-127">TABLE_PROPID</span></span>|<span data-ttu-id="65f6e-128">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-128">Int64</span></span>|  
|<span data-ttu-id="65f6e-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="65f6e-129">DATE_CREATED</span></span>|<span data-ttu-id="65f6e-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="65f6e-130">DateTime</span></span>|  
|<span data-ttu-id="65f6e-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="65f6e-131">DATE_MODIFIED</span></span>|<span data-ttu-id="65f6e-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="65f6e-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="65f6e-133">Colonnes</span><span class="sxs-lookup"><span data-stu-id="65f6e-133">Columns</span></span>  
  
|<span data-ttu-id="65f6e-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="65f6e-134">ColumnName</span></span>|<span data-ttu-id="65f6e-135">Type de données</span><span class="sxs-lookup"><span data-stu-id="65f6e-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="65f6e-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-136">TABLE_CATALOG</span></span>|<span data-ttu-id="65f6e-137">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-137">String</span></span>|  
|<span data-ttu-id="65f6e-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="65f6e-139">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-139">String</span></span>|  
|<span data-ttu-id="65f6e-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-140">TABLE_NAME</span></span>|<span data-ttu-id="65f6e-141">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-141">String</span></span>|  
|<span data-ttu-id="65f6e-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-142">COLUMN_NAME</span></span>|<span data-ttu-id="65f6e-143">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-143">String</span></span>|  
|<span data-ttu-id="65f6e-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="65f6e-144">COLUMN_GUID</span></span>|<span data-ttu-id="65f6e-145">Guid</span><span class="sxs-lookup"><span data-stu-id="65f6e-145">Guid</span></span>|  
|<span data-ttu-id="65f6e-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="65f6e-146">COLUMN_PROPID</span></span>|<span data-ttu-id="65f6e-147">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-147">Int64</span></span>|  
|<span data-ttu-id="65f6e-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="65f6e-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="65f6e-149">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-149">Int64</span></span>|  
|<span data-ttu-id="65f6e-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="65f6e-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="65f6e-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-151">Boolean</span></span>|  
|<span data-ttu-id="65f6e-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="65f6e-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="65f6e-153">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-153">String</span></span>|  
|<span data-ttu-id="65f6e-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="65f6e-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="65f6e-155">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-155">Int64</span></span>|  
|<span data-ttu-id="65f6e-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="65f6e-156">IS_NULLABLE</span></span>|<span data-ttu-id="65f6e-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-157">Boolean</span></span>|  
|<span data-ttu-id="65f6e-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="65f6e-158">DATA_TYPE</span></span>|<span data-ttu-id="65f6e-159">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-159">Int32</span></span>|  
|<span data-ttu-id="65f6e-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="65f6e-160">TYPE_GUID</span></span>|<span data-ttu-id="65f6e-161">Guid</span><span class="sxs-lookup"><span data-stu-id="65f6e-161">Guid</span></span>|  
|<span data-ttu-id="65f6e-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="65f6e-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="65f6e-163">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-163">Int64</span></span>|  
|<span data-ttu-id="65f6e-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="65f6e-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="65f6e-165">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-165">Int64</span></span>|  
|<span data-ttu-id="65f6e-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="65f6e-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="65f6e-167">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-167">Int32</span></span>|  
|<span data-ttu-id="65f6e-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="65f6e-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="65f6e-169">Int16</span><span class="sxs-lookup"><span data-stu-id="65f6e-169">Int16</span></span>|  
|<span data-ttu-id="65f6e-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="65f6e-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="65f6e-171">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-171">Int64</span></span>|  
|<span data-ttu-id="65f6e-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="65f6e-173">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-173">String</span></span>|  
|<span data-ttu-id="65f6e-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="65f6e-175">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-175">String</span></span>|  
|<span data-ttu-id="65f6e-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="65f6e-177">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-177">String</span></span>|  
|<span data-ttu-id="65f6e-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="65f6e-179">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-179">String</span></span>|  
|<span data-ttu-id="65f6e-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="65f6e-181">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-181">String</span></span>|  
|<span data-ttu-id="65f6e-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-182">COLLATION_NAME</span></span>|<span data-ttu-id="65f6e-183">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-183">String</span></span>|  
|<span data-ttu-id="65f6e-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="65f6e-185">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-185">String</span></span>|  
|<span data-ttu-id="65f6e-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="65f6e-187">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-187">String</span></span>|  
|<span data-ttu-id="65f6e-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-188">DOMAIN_NAME</span></span>|<span data-ttu-id="65f6e-189">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-189">String</span></span>|  
|<span data-ttu-id="65f6e-190">Description</span><span class="sxs-lookup"><span data-stu-id="65f6e-190">DESCRIPTION</span></span>|<span data-ttu-id="65f6e-191">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-191">String</span></span>|  
|<span data-ttu-id="65f6e-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="65f6e-192">COLUMN_LCID</span></span>|<span data-ttu-id="65f6e-193">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-193">Int32</span></span>|  
|<span data-ttu-id="65f6e-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="65f6e-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="65f6e-195">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-195">Int32</span></span>|  
|<span data-ttu-id="65f6e-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="65f6e-196">COLUMN_SORTID</span></span>|<span data-ttu-id="65f6e-197">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-197">Int32</span></span>|  
|<span data-ttu-id="65f6e-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="65f6e-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="65f6e-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="65f6e-199">Byte[]</span></span>|  
|<span data-ttu-id="65f6e-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="65f6e-200">IS_COMPUTED</span></span>|<span data-ttu-id="65f6e-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="65f6e-202">Procédures</span><span class="sxs-lookup"><span data-stu-id="65f6e-202">Procedures</span></span>  
  
|<span data-ttu-id="65f6e-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="65f6e-203">ColumnName</span></span>|<span data-ttu-id="65f6e-204">Type de données</span><span class="sxs-lookup"><span data-stu-id="65f6e-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="65f6e-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="65f6e-206">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-206">String</span></span>|  
|<span data-ttu-id="65f6e-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="65f6e-208">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-208">String</span></span>|  
|<span data-ttu-id="65f6e-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="65f6e-210">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-210">String</span></span>|  
|<span data-ttu-id="65f6e-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="65f6e-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="65f6e-212">Int16</span><span class="sxs-lookup"><span data-stu-id="65f6e-212">Int16</span></span>|  
|<span data-ttu-id="65f6e-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="65f6e-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="65f6e-214">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-214">String</span></span>|  
|<span data-ttu-id="65f6e-215">Description</span><span class="sxs-lookup"><span data-stu-id="65f6e-215">DESCRIPTION</span></span>|<span data-ttu-id="65f6e-216">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-216">String</span></span>|  
|<span data-ttu-id="65f6e-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="65f6e-217">DATE_CREATED</span></span>|<span data-ttu-id="65f6e-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="65f6e-218">DateTime</span></span>|  
|<span data-ttu-id="65f6e-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="65f6e-219">DATE_MODIFIED</span></span>|<span data-ttu-id="65f6e-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="65f6e-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="65f6e-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="65f6e-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="65f6e-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="65f6e-222">ColumnName</span></span>|<span data-ttu-id="65f6e-223">Type de données</span><span class="sxs-lookup"><span data-stu-id="65f6e-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="65f6e-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="65f6e-225">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-225">String</span></span>|  
|<span data-ttu-id="65f6e-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="65f6e-227">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-227">String</span></span>|  
|<span data-ttu-id="65f6e-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="65f6e-229">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-229">String</span></span>|  
|<span data-ttu-id="65f6e-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-230">PARAMETER_NAME</span></span>|<span data-ttu-id="65f6e-231">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-231">String</span></span>|  
|<span data-ttu-id="65f6e-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="65f6e-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="65f6e-233">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-233">Int32</span></span>|  
|<span data-ttu-id="65f6e-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="65f6e-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="65f6e-235">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-235">Int32</span></span>|  
|<span data-ttu-id="65f6e-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="65f6e-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="65f6e-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-237">Boolean</span></span>|  
|<span data-ttu-id="65f6e-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="65f6e-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="65f6e-239">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-239">String</span></span>|  
|<span data-ttu-id="65f6e-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="65f6e-240">IS_NULLABLE</span></span>|<span data-ttu-id="65f6e-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-241">Boolean</span></span>|  
|<span data-ttu-id="65f6e-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="65f6e-242">DATA_TYPE</span></span>|<span data-ttu-id="65f6e-243">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-243">Int32</span></span>|  
|<span data-ttu-id="65f6e-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="65f6e-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="65f6e-245">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-245">Int64</span></span>|  
|<span data-ttu-id="65f6e-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="65f6e-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="65f6e-247">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-247">Int64</span></span>|  
|<span data-ttu-id="65f6e-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="65f6e-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="65f6e-249">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-249">Int32</span></span>|  
|<span data-ttu-id="65f6e-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="65f6e-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="65f6e-251">Int16</span><span class="sxs-lookup"><span data-stu-id="65f6e-251">Int16</span></span>|  
|<span data-ttu-id="65f6e-252">Description</span><span class="sxs-lookup"><span data-stu-id="65f6e-252">DESCRIPTION</span></span>|<span data-ttu-id="65f6e-253">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-253">String</span></span>|  
|<span data-ttu-id="65f6e-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-254">TYPE_NAME</span></span>|<span data-ttu-id="65f6e-255">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-255">String</span></span>|  
|<span data-ttu-id="65f6e-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="65f6e-257">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="65f6e-258">Catalogue</span><span class="sxs-lookup"><span data-stu-id="65f6e-258">Catalog</span></span>  
  
|<span data-ttu-id="65f6e-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="65f6e-259">ColumnName</span></span>|<span data-ttu-id="65f6e-260">Type de données</span><span class="sxs-lookup"><span data-stu-id="65f6e-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="65f6e-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-261">CATALOG_NAME</span></span>|<span data-ttu-id="65f6e-262">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-262">String</span></span>|  
|<span data-ttu-id="65f6e-263">Description</span><span class="sxs-lookup"><span data-stu-id="65f6e-263">DESCRIPTION</span></span>|<span data-ttu-id="65f6e-264">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="65f6e-265">Index</span><span class="sxs-lookup"><span data-stu-id="65f6e-265">Indexes</span></span>  
  
|<span data-ttu-id="65f6e-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="65f6e-266">ColumnName</span></span>|<span data-ttu-id="65f6e-267">Type de données</span><span class="sxs-lookup"><span data-stu-id="65f6e-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="65f6e-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-268">TABLE_CATALOG</span></span>|<span data-ttu-id="65f6e-269">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-269">String</span></span>|  
|<span data-ttu-id="65f6e-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="65f6e-271">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-271">String</span></span>|  
|<span data-ttu-id="65f6e-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-272">TABLE_NAME</span></span>|<span data-ttu-id="65f6e-273">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-273">String</span></span>|  
|<span data-ttu-id="65f6e-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-274">INDEX_CATALOG</span></span>|<span data-ttu-id="65f6e-275">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-275">String</span></span>|  
|<span data-ttu-id="65f6e-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="65f6e-277">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-277">String</span></span>|  
|<span data-ttu-id="65f6e-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-278">INDEX_NAME</span></span>|<span data-ttu-id="65f6e-279">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-279">String</span></span>|  
|<span data-ttu-id="65f6e-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="65f6e-280">PRIMARY_KEY</span></span>|<span data-ttu-id="65f6e-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-281">Boolean</span></span>|  
|<span data-ttu-id="65f6e-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="65f6e-282">UNIQUE</span></span>|<span data-ttu-id="65f6e-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-283">Boolean</span></span>|  
|<span data-ttu-id="65f6e-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="65f6e-284">CLUSTERED</span></span>|<span data-ttu-id="65f6e-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-285">Boolean</span></span>|  
|<span data-ttu-id="65f6e-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="65f6e-286">TYPE</span></span>|<span data-ttu-id="65f6e-287">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-287">Int32</span></span>|  
|<span data-ttu-id="65f6e-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="65f6e-288">FILL_FACTOR</span></span>|<span data-ttu-id="65f6e-289">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-289">Int32</span></span>|  
|<span data-ttu-id="65f6e-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="65f6e-290">INITIAL_SIZE</span></span>|<span data-ttu-id="65f6e-291">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-291">Int32</span></span>|  
|<span data-ttu-id="65f6e-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="65f6e-292">NULLS</span></span>|<span data-ttu-id="65f6e-293">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-293">Int32</span></span>|  
|<span data-ttu-id="65f6e-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="65f6e-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="65f6e-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-295">Boolean</span></span>|  
|<span data-ttu-id="65f6e-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="65f6e-296">AUTO_UPDATE</span></span>|<span data-ttu-id="65f6e-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-297">Boolean</span></span>|  
|<span data-ttu-id="65f6e-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="65f6e-298">NULL_COLLATION</span></span>|<span data-ttu-id="65f6e-299">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-299">Int32</span></span>|  
|<span data-ttu-id="65f6e-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="65f6e-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="65f6e-301">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-301">Int64</span></span>|  
|<span data-ttu-id="65f6e-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-302">COLUMN_NAME</span></span>|<span data-ttu-id="65f6e-303">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-303">String</span></span>|  
|<span data-ttu-id="65f6e-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="65f6e-304">COLUMN_GUID</span></span>|<span data-ttu-id="65f6e-305">Guid</span><span class="sxs-lookup"><span data-stu-id="65f6e-305">Guid</span></span>|  
|<span data-ttu-id="65f6e-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="65f6e-306">COLUMN_PROPID</span></span>|<span data-ttu-id="65f6e-307">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-307">Int64</span></span>|  
|<span data-ttu-id="65f6e-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="65f6e-308">COLLATION</span></span>|<span data-ttu-id="65f6e-309">Int16</span><span class="sxs-lookup"><span data-stu-id="65f6e-309">Int16</span></span>|  
|<span data-ttu-id="65f6e-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="65f6e-310">CARDINALITY</span></span>|<span data-ttu-id="65f6e-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="65f6e-311">Decimal</span></span>|  
|<span data-ttu-id="65f6e-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="65f6e-312">PAGES</span></span>|<span data-ttu-id="65f6e-313">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-313">Int32</span></span>|  
|<span data-ttu-id="65f6e-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="65f6e-314">FILTER_CONDITION</span></span>|<span data-ttu-id="65f6e-315">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-315">String</span></span>|  
|<span data-ttu-id="65f6e-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="65f6e-316">INTEGRATED</span></span>|<span data-ttu-id="65f6e-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="65f6e-318">Fournisseur Microsoft Oracle OLE DB</span><span class="sxs-lookup"><span data-stu-id="65f6e-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="65f6e-319">Le pilote Microsoft Oracle OLE DB prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="65f6e-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="65f6e-320">Tables</span><span class="sxs-lookup"><span data-stu-id="65f6e-320">Tables</span></span>  
  
- <span data-ttu-id="65f6e-321">Colonnes</span><span class="sxs-lookup"><span data-stu-id="65f6e-321">Columns</span></span>  
  
- <span data-ttu-id="65f6e-322">Procédures</span><span class="sxs-lookup"><span data-stu-id="65f6e-322">Procedures</span></span>  
  
- <span data-ttu-id="65f6e-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="65f6e-323">ProcedureColumns</span></span>  
  
- <span data-ttu-id="65f6e-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="65f6e-324">ProcedureParameters</span></span>  
  
- <span data-ttu-id="65f6e-325">Affichages</span><span class="sxs-lookup"><span data-stu-id="65f6e-325">Views</span></span>  
  
- <span data-ttu-id="65f6e-326">Index</span><span class="sxs-lookup"><span data-stu-id="65f6e-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="65f6e-327">Tables</span><span class="sxs-lookup"><span data-stu-id="65f6e-327">Tables</span></span>  
  
|<span data-ttu-id="65f6e-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="65f6e-328">ColumnName</span></span>|<span data-ttu-id="65f6e-329">Type de données</span><span class="sxs-lookup"><span data-stu-id="65f6e-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="65f6e-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-330">TABLE_CATALOG</span></span>|<span data-ttu-id="65f6e-331">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-331">String</span></span>|  
|<span data-ttu-id="65f6e-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="65f6e-333">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-333">String</span></span>|  
|<span data-ttu-id="65f6e-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-334">TABLE_NAME</span></span>|<span data-ttu-id="65f6e-335">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-335">String</span></span>|  
|<span data-ttu-id="65f6e-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="65f6e-336">TABLE_TYPE</span></span>|<span data-ttu-id="65f6e-337">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-337">String</span></span>|  
|<span data-ttu-id="65f6e-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="65f6e-338">TABLE_GUID</span></span>|<span data-ttu-id="65f6e-339">Guid</span><span class="sxs-lookup"><span data-stu-id="65f6e-339">Guid</span></span>|  
|<span data-ttu-id="65f6e-340">Description</span><span class="sxs-lookup"><span data-stu-id="65f6e-340">DESCRIPTION</span></span>|<span data-ttu-id="65f6e-341">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-341">String</span></span>|  
|<span data-ttu-id="65f6e-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="65f6e-342">TABLE_PROPID</span></span>|<span data-ttu-id="65f6e-343">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-343">Int64</span></span>|  
|<span data-ttu-id="65f6e-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="65f6e-344">DATE_CREATED</span></span>|<span data-ttu-id="65f6e-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="65f6e-345">DateTime</span></span>|  
|<span data-ttu-id="65f6e-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="65f6e-346">DATE_MODIFIED</span></span>|<span data-ttu-id="65f6e-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="65f6e-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="65f6e-348">Colonnes</span><span class="sxs-lookup"><span data-stu-id="65f6e-348">Columns</span></span>  
  
|<span data-ttu-id="65f6e-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="65f6e-349">ColumnName</span></span>|<span data-ttu-id="65f6e-350">Type de données</span><span class="sxs-lookup"><span data-stu-id="65f6e-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="65f6e-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-351">TABLE_CATALOG</span></span>|<span data-ttu-id="65f6e-352">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-352">String</span></span>|  
|<span data-ttu-id="65f6e-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="65f6e-354">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-354">String</span></span>|  
|<span data-ttu-id="65f6e-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-355">TABLE_NAME</span></span>|<span data-ttu-id="65f6e-356">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-356">String</span></span>|  
|<span data-ttu-id="65f6e-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-357">COLUMN_NAME</span></span>|<span data-ttu-id="65f6e-358">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-358">String</span></span>|  
|<span data-ttu-id="65f6e-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="65f6e-359">COLUMN_GUID</span></span>|<span data-ttu-id="65f6e-360">Guid</span><span class="sxs-lookup"><span data-stu-id="65f6e-360">Guid</span></span>|  
|<span data-ttu-id="65f6e-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="65f6e-361">COLUMN_PROPID</span></span>|<span data-ttu-id="65f6e-362">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-362">Int64</span></span>|  
|<span data-ttu-id="65f6e-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="65f6e-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="65f6e-364">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-364">Int64</span></span>|  
|<span data-ttu-id="65f6e-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="65f6e-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="65f6e-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-366">Boolean</span></span>|  
|<span data-ttu-id="65f6e-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="65f6e-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="65f6e-368">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-368">String</span></span>|  
|<span data-ttu-id="65f6e-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="65f6e-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="65f6e-370">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-370">Int64</span></span>|  
|<span data-ttu-id="65f6e-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="65f6e-371">IS_NULLABLE</span></span>|<span data-ttu-id="65f6e-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-372">Boolean</span></span>|  
|<span data-ttu-id="65f6e-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="65f6e-373">DATA_TYPE</span></span>|<span data-ttu-id="65f6e-374">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-374">Int32</span></span>|  
|<span data-ttu-id="65f6e-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="65f6e-375">TYPE_GUID</span></span>|<span data-ttu-id="65f6e-376">Guid</span><span class="sxs-lookup"><span data-stu-id="65f6e-376">Guid</span></span>|  
|<span data-ttu-id="65f6e-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="65f6e-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="65f6e-378">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-378">Int64</span></span>|  
|<span data-ttu-id="65f6e-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="65f6e-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="65f6e-380">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-380">Int64</span></span>|  
|<span data-ttu-id="65f6e-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="65f6e-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="65f6e-382">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-382">Int32</span></span>|  
|<span data-ttu-id="65f6e-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="65f6e-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="65f6e-384">Int16</span><span class="sxs-lookup"><span data-stu-id="65f6e-384">Int16</span></span>|  
|<span data-ttu-id="65f6e-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="65f6e-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="65f6e-386">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-386">Int64</span></span>|  
|<span data-ttu-id="65f6e-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="65f6e-388">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-388">String</span></span>|  
|<span data-ttu-id="65f6e-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="65f6e-390">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-390">String</span></span>|  
|<span data-ttu-id="65f6e-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="65f6e-392">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-392">String</span></span>|  
|<span data-ttu-id="65f6e-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="65f6e-394">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-394">String</span></span>|  
|<span data-ttu-id="65f6e-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="65f6e-396">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-396">String</span></span>|  
|<span data-ttu-id="65f6e-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-397">COLLATION_NAME</span></span>|<span data-ttu-id="65f6e-398">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-398">String</span></span>|  
|<span data-ttu-id="65f6e-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="65f6e-400">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-400">String</span></span>|  
|<span data-ttu-id="65f6e-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="65f6e-402">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-402">String</span></span>|  
|<span data-ttu-id="65f6e-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-403">DOMAIN_NAME</span></span>|<span data-ttu-id="65f6e-404">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-404">String</span></span>|  
|<span data-ttu-id="65f6e-405">Description</span><span class="sxs-lookup"><span data-stu-id="65f6e-405">DESCRIPTION</span></span>|<span data-ttu-id="65f6e-406">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="65f6e-407">Procédures</span><span class="sxs-lookup"><span data-stu-id="65f6e-407">Procedures</span></span>  
  
|<span data-ttu-id="65f6e-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="65f6e-408">ColumnName</span></span>|<span data-ttu-id="65f6e-409">Type de données</span><span class="sxs-lookup"><span data-stu-id="65f6e-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="65f6e-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="65f6e-411">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-411">String</span></span>|  
|<span data-ttu-id="65f6e-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="65f6e-413">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-413">String</span></span>|  
|<span data-ttu-id="65f6e-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="65f6e-415">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-415">String</span></span>|  
|<span data-ttu-id="65f6e-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="65f6e-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="65f6e-417">Int16</span><span class="sxs-lookup"><span data-stu-id="65f6e-417">Int16</span></span>|  
|<span data-ttu-id="65f6e-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="65f6e-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="65f6e-419">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-419">String</span></span>|  
|<span data-ttu-id="65f6e-420">Description</span><span class="sxs-lookup"><span data-stu-id="65f6e-420">DESCRIPTION</span></span>|<span data-ttu-id="65f6e-421">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-421">String</span></span>|  
|<span data-ttu-id="65f6e-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="65f6e-422">DATE_CREATED</span></span>|<span data-ttu-id="65f6e-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="65f6e-423">DateTime</span></span>|  
|<span data-ttu-id="65f6e-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="65f6e-424">DATE_MODIFIED</span></span>|<span data-ttu-id="65f6e-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="65f6e-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="65f6e-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="65f6e-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="65f6e-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="65f6e-427">ColumnName</span></span>|<span data-ttu-id="65f6e-428">Type de données</span><span class="sxs-lookup"><span data-stu-id="65f6e-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="65f6e-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="65f6e-430">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-430">String</span></span>|  
|<span data-ttu-id="65f6e-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="65f6e-432">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-432">String</span></span>|  
|<span data-ttu-id="65f6e-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="65f6e-434">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-434">String</span></span>|  
|<span data-ttu-id="65f6e-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-435">COLUMN_NAME</span></span>|<span data-ttu-id="65f6e-436">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-436">String</span></span>|  
|<span data-ttu-id="65f6e-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="65f6e-437">COLUMN_GUID</span></span>|<span data-ttu-id="65f6e-438">Guid</span><span class="sxs-lookup"><span data-stu-id="65f6e-438">Guid</span></span>|  
|<span data-ttu-id="65f6e-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="65f6e-439">COLUMN_PROPID</span></span>|<span data-ttu-id="65f6e-440">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-440">Int64</span></span>|  
|<span data-ttu-id="65f6e-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="65f6e-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="65f6e-442">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-442">Int64</span></span>|  
|<span data-ttu-id="65f6e-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="65f6e-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="65f6e-444">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-444">Int64</span></span>|  
|<span data-ttu-id="65f6e-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="65f6e-445">IS_NULLABLE</span></span>|<span data-ttu-id="65f6e-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-446">Boolean</span></span>|  
|<span data-ttu-id="65f6e-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="65f6e-447">DATA_TYPE</span></span>|<span data-ttu-id="65f6e-448">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-448">Int32</span></span>|  
|<span data-ttu-id="65f6e-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="65f6e-449">TYPE_GUID</span></span>|<span data-ttu-id="65f6e-450">Guid</span><span class="sxs-lookup"><span data-stu-id="65f6e-450">Guid</span></span>|  
|<span data-ttu-id="65f6e-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="65f6e-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="65f6e-452">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-452">Int64</span></span>|  
|<span data-ttu-id="65f6e-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="65f6e-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="65f6e-454">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-454">Int64</span></span>|  
|<span data-ttu-id="65f6e-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="65f6e-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="65f6e-456">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-456">Int32</span></span>|  
|<span data-ttu-id="65f6e-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="65f6e-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="65f6e-458">Int16</span><span class="sxs-lookup"><span data-stu-id="65f6e-458">Int16</span></span>|  
|<span data-ttu-id="65f6e-459">Description</span><span class="sxs-lookup"><span data-stu-id="65f6e-459">DESCRIPTION</span></span>|<span data-ttu-id="65f6e-460">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-460">String</span></span>|  
|<span data-ttu-id="65f6e-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="65f6e-461">OVERLOAD</span></span>|<span data-ttu-id="65f6e-462">Int16</span><span class="sxs-lookup"><span data-stu-id="65f6e-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="65f6e-463">Affichages</span><span class="sxs-lookup"><span data-stu-id="65f6e-463">Views</span></span>  
  
|<span data-ttu-id="65f6e-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="65f6e-464">ColumnName</span></span>|<span data-ttu-id="65f6e-465">Type de données</span><span class="sxs-lookup"><span data-stu-id="65f6e-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="65f6e-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-466">TABLE_CATALOG</span></span>|<span data-ttu-id="65f6e-467">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-467">String</span></span>|  
|<span data-ttu-id="65f6e-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="65f6e-469">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-469">String</span></span>|  
|<span data-ttu-id="65f6e-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-470">TABLE_NAME</span></span>|<span data-ttu-id="65f6e-471">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-471">String</span></span>|  
|<span data-ttu-id="65f6e-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="65f6e-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="65f6e-473">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-473">String</span></span>|  
|<span data-ttu-id="65f6e-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="65f6e-474">CHECK_OPTION</span></span>|<span data-ttu-id="65f6e-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-475">Boolean</span></span>|  
|<span data-ttu-id="65f6e-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="65f6e-476">IS_UPDATABLE</span></span>|<span data-ttu-id="65f6e-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-477">Boolean</span></span>|  
|<span data-ttu-id="65f6e-478">Description</span><span class="sxs-lookup"><span data-stu-id="65f6e-478">DESCRIPTION</span></span>|<span data-ttu-id="65f6e-479">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-479">String</span></span>|  
|<span data-ttu-id="65f6e-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="65f6e-480">DATE_CREATED</span></span>|<span data-ttu-id="65f6e-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="65f6e-481">DateTime</span></span>|  
|<span data-ttu-id="65f6e-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="65f6e-482">DATE_MODIFIED</span></span>|<span data-ttu-id="65f6e-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="65f6e-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="65f6e-484">Index</span><span class="sxs-lookup"><span data-stu-id="65f6e-484">Indexes</span></span>  
  
|<span data-ttu-id="65f6e-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="65f6e-485">ColumnName</span></span>|<span data-ttu-id="65f6e-486">Type de données</span><span class="sxs-lookup"><span data-stu-id="65f6e-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="65f6e-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-487">TABLE_CATALOG</span></span>|<span data-ttu-id="65f6e-488">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-488">String</span></span>|  
|<span data-ttu-id="65f6e-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="65f6e-490">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-490">String</span></span>|  
|<span data-ttu-id="65f6e-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-491">TABLE_NAME</span></span>|<span data-ttu-id="65f6e-492">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-492">String</span></span>|  
|<span data-ttu-id="65f6e-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-493">INDEX_CATALOG</span></span>|<span data-ttu-id="65f6e-494">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-494">String</span></span>|  
|<span data-ttu-id="65f6e-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="65f6e-496">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-496">String</span></span>|  
|<span data-ttu-id="65f6e-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-497">INDEX_NAME</span></span>|<span data-ttu-id="65f6e-498">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-498">String</span></span>|  
|<span data-ttu-id="65f6e-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="65f6e-499">PRIMARY_KEY</span></span>|<span data-ttu-id="65f6e-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-500">Boolean</span></span>|  
|<span data-ttu-id="65f6e-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="65f6e-501">UNIQUE</span></span>|<span data-ttu-id="65f6e-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-502">Boolean</span></span>|  
|<span data-ttu-id="65f6e-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="65f6e-503">CLUSTERED</span></span>|<span data-ttu-id="65f6e-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-504">Boolean</span></span>|  
|<span data-ttu-id="65f6e-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="65f6e-505">TYPE</span></span>|<span data-ttu-id="65f6e-506">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-506">Int32</span></span>|  
|<span data-ttu-id="65f6e-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="65f6e-507">FILL_FACTOR</span></span>|<span data-ttu-id="65f6e-508">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-508">Int32</span></span>|  
|<span data-ttu-id="65f6e-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="65f6e-509">INITIAL_SIZE</span></span>|<span data-ttu-id="65f6e-510">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-510">Int32</span></span>|  
|<span data-ttu-id="65f6e-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="65f6e-511">NULLS</span></span>|<span data-ttu-id="65f6e-512">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-512">Int32</span></span>|  
|<span data-ttu-id="65f6e-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="65f6e-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="65f6e-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-514">Boolean</span></span>|  
|<span data-ttu-id="65f6e-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="65f6e-515">AUTO_UPDATE</span></span>|<span data-ttu-id="65f6e-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-516">Boolean</span></span>|  
|<span data-ttu-id="65f6e-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="65f6e-517">NULL_COLLATION</span></span>|<span data-ttu-id="65f6e-518">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-518">Int32</span></span>|  
|<span data-ttu-id="65f6e-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="65f6e-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="65f6e-520">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-520">Int64</span></span>|  
|<span data-ttu-id="65f6e-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-521">COLUMN_NAME</span></span>|<span data-ttu-id="65f6e-522">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-522">String</span></span>|  
|<span data-ttu-id="65f6e-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="65f6e-523">COLUMN_GUID</span></span>|<span data-ttu-id="65f6e-524">Guid</span><span class="sxs-lookup"><span data-stu-id="65f6e-524">Guid</span></span>|  
|<span data-ttu-id="65f6e-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="65f6e-525">COLUMN_PROPID</span></span>|<span data-ttu-id="65f6e-526">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-526">Int64</span></span>|  
|<span data-ttu-id="65f6e-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="65f6e-527">COLLATION</span></span>|<span data-ttu-id="65f6e-528">Int16</span><span class="sxs-lookup"><span data-stu-id="65f6e-528">Int16</span></span>|  
|<span data-ttu-id="65f6e-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="65f6e-529">CARDINALITY</span></span>|<span data-ttu-id="65f6e-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="65f6e-530">Decimal</span></span>|  
|<span data-ttu-id="65f6e-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="65f6e-531">PAGES</span></span>|<span data-ttu-id="65f6e-532">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-532">Int32</span></span>|  
|<span data-ttu-id="65f6e-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="65f6e-533">FILTER_CONDITION</span></span>|<span data-ttu-id="65f6e-534">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-534">String</span></span>|  
|<span data-ttu-id="65f6e-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="65f6e-535">INTEGRATED</span></span>|<span data-ttu-id="65f6e-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="65f6e-537">Fournisseur Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="65f6e-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="65f6e-538">Le pilote Microsoft Jet OLE DB prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="65f6e-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="65f6e-539">Tables</span><span class="sxs-lookup"><span data-stu-id="65f6e-539">Tables</span></span>  
  
- <span data-ttu-id="65f6e-540">Colonnes</span><span class="sxs-lookup"><span data-stu-id="65f6e-540">Columns</span></span>  
  
- <span data-ttu-id="65f6e-541">Procédures</span><span class="sxs-lookup"><span data-stu-id="65f6e-541">Procedures</span></span>  
  
- <span data-ttu-id="65f6e-542">Affichages</span><span class="sxs-lookup"><span data-stu-id="65f6e-542">Views</span></span>  
  
- <span data-ttu-id="65f6e-543">Index</span><span class="sxs-lookup"><span data-stu-id="65f6e-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="65f6e-544">Tables</span><span class="sxs-lookup"><span data-stu-id="65f6e-544">Tables</span></span>  
  
|<span data-ttu-id="65f6e-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="65f6e-545">ColumnName</span></span>|<span data-ttu-id="65f6e-546">Type de données</span><span class="sxs-lookup"><span data-stu-id="65f6e-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="65f6e-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-547">TABLE_CATALOG</span></span>|<span data-ttu-id="65f6e-548">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-548">String</span></span>|  
|<span data-ttu-id="65f6e-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="65f6e-550">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-550">String</span></span>|  
|<span data-ttu-id="65f6e-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-551">TABLE_NAME</span></span>|<span data-ttu-id="65f6e-552">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-552">String</span></span>|  
|<span data-ttu-id="65f6e-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="65f6e-553">TABLE_TYPE</span></span>|<span data-ttu-id="65f6e-554">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-554">String</span></span>|  
|<span data-ttu-id="65f6e-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="65f6e-555">TABLE_GUID</span></span>|<span data-ttu-id="65f6e-556">Guid</span><span class="sxs-lookup"><span data-stu-id="65f6e-556">Guid</span></span>|  
|<span data-ttu-id="65f6e-557">Description</span><span class="sxs-lookup"><span data-stu-id="65f6e-557">DESCRIPTION</span></span>|<span data-ttu-id="65f6e-558">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-558">String</span></span>|  
|<span data-ttu-id="65f6e-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="65f6e-559">TABLE_PROPID</span></span>|<span data-ttu-id="65f6e-560">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-560">Int64</span></span>|  
|<span data-ttu-id="65f6e-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="65f6e-561">DATE_CREATED</span></span>|<span data-ttu-id="65f6e-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="65f6e-562">DateTime</span></span>|  
|<span data-ttu-id="65f6e-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="65f6e-563">DATE_MODIFIED</span></span>|<span data-ttu-id="65f6e-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="65f6e-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="65f6e-565">Colonnes</span><span class="sxs-lookup"><span data-stu-id="65f6e-565">Columns</span></span>  
  
|<span data-ttu-id="65f6e-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="65f6e-566">ColumnName</span></span>|<span data-ttu-id="65f6e-567">Type de données</span><span class="sxs-lookup"><span data-stu-id="65f6e-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="65f6e-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-568">TABLE_CATALOG</span></span>|<span data-ttu-id="65f6e-569">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-569">String</span></span>|  
|<span data-ttu-id="65f6e-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="65f6e-571">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-571">String</span></span>|  
|<span data-ttu-id="65f6e-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-572">TABLE_NAME</span></span>|<span data-ttu-id="65f6e-573">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-573">String</span></span>|  
|<span data-ttu-id="65f6e-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-574">COLUMN_NAME</span></span>|<span data-ttu-id="65f6e-575">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-575">String</span></span>|  
|<span data-ttu-id="65f6e-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="65f6e-576">COLUMN_GUID</span></span>|<span data-ttu-id="65f6e-577">Guid</span><span class="sxs-lookup"><span data-stu-id="65f6e-577">Guid</span></span>|  
|<span data-ttu-id="65f6e-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="65f6e-578">COLUMN_PROPID</span></span>|<span data-ttu-id="65f6e-579">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-579">Int64</span></span>|  
|<span data-ttu-id="65f6e-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="65f6e-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="65f6e-581">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-581">Int64</span></span>|  
|<span data-ttu-id="65f6e-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="65f6e-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="65f6e-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-583">Boolean</span></span>|  
|<span data-ttu-id="65f6e-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="65f6e-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="65f6e-585">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-585">String</span></span>|  
|<span data-ttu-id="65f6e-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="65f6e-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="65f6e-587">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-587">Int64</span></span>|  
|<span data-ttu-id="65f6e-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="65f6e-588">IS_NULLABLE</span></span>|<span data-ttu-id="65f6e-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-589">Boolean</span></span>|  
|<span data-ttu-id="65f6e-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="65f6e-590">DATA_TYPE</span></span>|<span data-ttu-id="65f6e-591">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-591">Int32</span></span>|  
|<span data-ttu-id="65f6e-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="65f6e-592">TYPE_GUID</span></span>|<span data-ttu-id="65f6e-593">Guid</span><span class="sxs-lookup"><span data-stu-id="65f6e-593">Guid</span></span>|  
|<span data-ttu-id="65f6e-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="65f6e-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="65f6e-595">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-595">Int64</span></span>|  
|<span data-ttu-id="65f6e-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="65f6e-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="65f6e-597">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-597">Int64</span></span>|  
|<span data-ttu-id="65f6e-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="65f6e-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="65f6e-599">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-599">Int32</span></span>|  
|<span data-ttu-id="65f6e-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="65f6e-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="65f6e-601">Int16</span><span class="sxs-lookup"><span data-stu-id="65f6e-601">Int16</span></span>|  
|<span data-ttu-id="65f6e-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="65f6e-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="65f6e-603">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-603">Int64</span></span>|  
|<span data-ttu-id="65f6e-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="65f6e-605">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-605">String</span></span>|  
|<span data-ttu-id="65f6e-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="65f6e-607">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-607">String</span></span>|  
|<span data-ttu-id="65f6e-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="65f6e-609">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-609">String</span></span>|  
|<span data-ttu-id="65f6e-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="65f6e-611">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-611">String</span></span>|  
|<span data-ttu-id="65f6e-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="65f6e-613">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-613">String</span></span>|  
|<span data-ttu-id="65f6e-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-614">COLLATION_NAME</span></span>|<span data-ttu-id="65f6e-615">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-615">String</span></span>|  
|<span data-ttu-id="65f6e-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="65f6e-617">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-617">String</span></span>|  
|<span data-ttu-id="65f6e-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="65f6e-619">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-619">String</span></span>|  
|<span data-ttu-id="65f6e-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-620">DOMAIN_NAME</span></span>|<span data-ttu-id="65f6e-621">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-621">String</span></span>|  
|<span data-ttu-id="65f6e-622">Description</span><span class="sxs-lookup"><span data-stu-id="65f6e-622">DESCRIPTION</span></span>|<span data-ttu-id="65f6e-623">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="65f6e-624">Procédures</span><span class="sxs-lookup"><span data-stu-id="65f6e-624">Procedures</span></span>  
  
|<span data-ttu-id="65f6e-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="65f6e-625">ColumnName</span></span>|<span data-ttu-id="65f6e-626">Type de données</span><span class="sxs-lookup"><span data-stu-id="65f6e-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="65f6e-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="65f6e-628">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-628">String</span></span>|  
|<span data-ttu-id="65f6e-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="65f6e-630">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-630">String</span></span>|  
|<span data-ttu-id="65f6e-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="65f6e-632">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-632">String</span></span>|  
|<span data-ttu-id="65f6e-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="65f6e-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="65f6e-634">Int16</span><span class="sxs-lookup"><span data-stu-id="65f6e-634">Int16</span></span>|  
|<span data-ttu-id="65f6e-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="65f6e-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="65f6e-636">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-636">String</span></span>|  
|<span data-ttu-id="65f6e-637">Description</span><span class="sxs-lookup"><span data-stu-id="65f6e-637">DESCRIPTION</span></span>|<span data-ttu-id="65f6e-638">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-638">String</span></span>|  
|<span data-ttu-id="65f6e-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="65f6e-639">DATE_CREATED</span></span>|<span data-ttu-id="65f6e-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="65f6e-640">DateTime</span></span>|  
|<span data-ttu-id="65f6e-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="65f6e-641">DATE_MODIFIED</span></span>|<span data-ttu-id="65f6e-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="65f6e-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="65f6e-643">Affichages</span><span class="sxs-lookup"><span data-stu-id="65f6e-643">Views</span></span>  
  
|<span data-ttu-id="65f6e-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="65f6e-644">ColumnName</span></span>|<span data-ttu-id="65f6e-645">Type de données</span><span class="sxs-lookup"><span data-stu-id="65f6e-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="65f6e-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-646">TABLE_CATALOG</span></span>|<span data-ttu-id="65f6e-647">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-647">String</span></span>|  
|<span data-ttu-id="65f6e-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="65f6e-649">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-649">String</span></span>|  
|<span data-ttu-id="65f6e-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-650">TABLE_NAME</span></span>|<span data-ttu-id="65f6e-651">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-651">String</span></span>|  
|<span data-ttu-id="65f6e-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="65f6e-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="65f6e-653">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-653">String</span></span>|  
|<span data-ttu-id="65f6e-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="65f6e-654">CHECK_OPTION</span></span>|<span data-ttu-id="65f6e-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-655">Boolean</span></span>|  
|<span data-ttu-id="65f6e-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="65f6e-656">IS_UPDATABLE</span></span>|<span data-ttu-id="65f6e-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-657">Boolean</span></span>|  
|<span data-ttu-id="65f6e-658">Description</span><span class="sxs-lookup"><span data-stu-id="65f6e-658">DESCRIPTION</span></span>|<span data-ttu-id="65f6e-659">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-659">String</span></span>|  
|<span data-ttu-id="65f6e-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="65f6e-660">DATE_CREATED</span></span>|<span data-ttu-id="65f6e-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="65f6e-661">DateTime</span></span>|  
|<span data-ttu-id="65f6e-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="65f6e-662">DATE_MODIFIED</span></span>|<span data-ttu-id="65f6e-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="65f6e-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="65f6e-664">Index</span><span class="sxs-lookup"><span data-stu-id="65f6e-664">Indexes</span></span>  
  
|<span data-ttu-id="65f6e-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="65f6e-665">ColumnName</span></span>|<span data-ttu-id="65f6e-666">Type de données</span><span class="sxs-lookup"><span data-stu-id="65f6e-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="65f6e-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-667">TABLE_CATALOG</span></span>|<span data-ttu-id="65f6e-668">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-668">String</span></span>|  
|<span data-ttu-id="65f6e-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="65f6e-670">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-670">String</span></span>|  
|<span data-ttu-id="65f6e-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-671">TABLE_NAME</span></span>|<span data-ttu-id="65f6e-672">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-672">String</span></span>|  
|<span data-ttu-id="65f6e-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="65f6e-673">INDEX_CATALOG</span></span>|<span data-ttu-id="65f6e-674">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-674">String</span></span>|  
|<span data-ttu-id="65f6e-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="65f6e-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="65f6e-676">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-676">String</span></span>|  
|<span data-ttu-id="65f6e-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-677">INDEX_NAME</span></span>|<span data-ttu-id="65f6e-678">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-678">String</span></span>|  
|<span data-ttu-id="65f6e-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="65f6e-679">PRIMARY_KEY</span></span>|<span data-ttu-id="65f6e-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-680">Boolean</span></span>|  
|<span data-ttu-id="65f6e-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="65f6e-681">UNIQUE</span></span>|<span data-ttu-id="65f6e-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-682">Boolean</span></span>|  
|<span data-ttu-id="65f6e-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="65f6e-683">CLUSTERED</span></span>|<span data-ttu-id="65f6e-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-684">Boolean</span></span>|  
|<span data-ttu-id="65f6e-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="65f6e-685">TYPE</span></span>|<span data-ttu-id="65f6e-686">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-686">Int32</span></span>|  
|<span data-ttu-id="65f6e-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="65f6e-687">FILL_FACTOR</span></span>|<span data-ttu-id="65f6e-688">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-688">Int32</span></span>|  
|<span data-ttu-id="65f6e-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="65f6e-689">INITIAL_SIZE</span></span>|<span data-ttu-id="65f6e-690">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-690">Int32</span></span>|  
|<span data-ttu-id="65f6e-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="65f6e-691">NULLS</span></span>|<span data-ttu-id="65f6e-692">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-692">Int32</span></span>|  
|<span data-ttu-id="65f6e-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="65f6e-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="65f6e-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-694">Boolean</span></span>|  
|<span data-ttu-id="65f6e-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="65f6e-695">AUTO_UPDATE</span></span>|<span data-ttu-id="65f6e-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-696">Boolean</span></span>|  
|<span data-ttu-id="65f6e-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="65f6e-697">NULL_COLLATION</span></span>|<span data-ttu-id="65f6e-698">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-698">Int32</span></span>|  
|<span data-ttu-id="65f6e-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="65f6e-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="65f6e-700">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-700">Int64</span></span>|  
|<span data-ttu-id="65f6e-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="65f6e-701">COLUMN_NAME</span></span>|<span data-ttu-id="65f6e-702">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-702">String</span></span>|  
|<span data-ttu-id="65f6e-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="65f6e-703">COLUMN_GUID</span></span>|<span data-ttu-id="65f6e-704">Guid</span><span class="sxs-lookup"><span data-stu-id="65f6e-704">Guid</span></span>|  
|<span data-ttu-id="65f6e-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="65f6e-705">COLUMN_PROPID</span></span>|<span data-ttu-id="65f6e-706">Int64</span><span class="sxs-lookup"><span data-stu-id="65f6e-706">Int64</span></span>|  
|<span data-ttu-id="65f6e-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="65f6e-707">COLLATION</span></span>|<span data-ttu-id="65f6e-708">Int16</span><span class="sxs-lookup"><span data-stu-id="65f6e-708">Int16</span></span>|  
|<span data-ttu-id="65f6e-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="65f6e-709">CARDINALITY</span></span>|<span data-ttu-id="65f6e-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="65f6e-710">Decimal</span></span>|  
|<span data-ttu-id="65f6e-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="65f6e-711">PAGES</span></span>|<span data-ttu-id="65f6e-712">Int32</span><span class="sxs-lookup"><span data-stu-id="65f6e-712">Int32</span></span>|  
|<span data-ttu-id="65f6e-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="65f6e-713">FILTER_CONDITION</span></span>|<span data-ttu-id="65f6e-714">String</span><span class="sxs-lookup"><span data-stu-id="65f6e-714">String</span></span>|  
|<span data-ttu-id="65f6e-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="65f6e-715">INTEGRATED</span></span>|<span data-ttu-id="65f6e-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="65f6e-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65f6e-717">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65f6e-717">See also</span></span>

- [<span data-ttu-id="65f6e-718">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="65f6e-718">ADO.NET Overview</span></span>](ado-net-overview.md)
