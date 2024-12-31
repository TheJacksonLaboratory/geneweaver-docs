
!!! warning "Work In Progress"
    [//]: # (TODO)
    This page is currently under construction, and not **all** tables in the data model
    are currently listed on this page. 

### Geneset Table
The geneset table is the heart of the geneweaver data model. The geneset table is 
contained in the `production` schema. The geneset table contains the following columns:
```mermaid
erDiagram
    geneset {
        bigint gs_id
        integer usr_id
        bigint file_id
        varchar gs_name
        varchar gs_abbreviation
        integer pub_id
        integer res_id
        integer cur_id
        varchar gs_description
        integer sp_id
        integer gs_count
        integer gs_threshold_type
        varchar gs_threshold
        varchar gs_groups
        varchar gs_attribution_old
        varchar gs_uri
        integer gs_gene_id_type
        date gs_created
        varchar admin_flag
        timestamp gs_updated
        varchar gs_status
        varchar gsv_qual
        integer gs_attribution
        boolean gs_is_edgelist
    }
```
##### Genes & Geneset Values
Geneset values are the genomic features in the geneset. The geneset values table is
contained in the `extsrc` schema. The geneset values table is an associative table
between the geneset table and the gene table. The geneset values table and the genes
table contain the following columns:
```mermaid
erDiagram
    geneset }o--|| geneset_value : hasA
    gene }o--|| geneset_value : hasA
    geneset_value {
        bigint gs_id
        bigint ode_gene_id
        numeric gsv_value
        bigint gsv_hits
        character_varying[] gsv_source_list
        numeric[] gsv_values_list
        boolean gsv_in_threshold
        date gsv_date
    }
    gene {
        bigint ode_gene_id
        varchar ode_ref_id
        integer gdb_id
        integer sp_id
        boolean ode_pref
        date ode_date
        bigint[] old_ode_gene_ids
    }
```


##### Files
Genesets are created from user uploaded files. The file table is contained in the
`production` schema. The file table contains the following columns:
```mermaid
erDiagram
    geneset ||--o{  file : createdFrom
    file {
        bigint file_id
        bigint file_size
        varchar file_uri
        text file_contents
        varchar file_comments
        date file_created
        text file_changes
    }
```

##### Species
Genesets are of a species, that is, the genomic features in the geneset are from a
specific species. The species table is contained in the `odestatic` schema. The species
table contains the following columns:
```mermaid
erDiagram
    geneset ||--o{ species: hasA
    species {
        integer sp_id
        varchar sp_name
        integer sp_taxid
        integer sp_ref_gdb_id
        date sp_date
        varchar sp_biomart_info
        text sp_source_data
    }
```

##### Tier (Curation Level)
Geneset tiers are indicated using the curation levels table. The curation levels table
is contained in the `odestatic` schema. The curation levels table contains the following
columns:
```mermaid
erDiagram
    geneset ||--o{  curation_levels: hasA
    curation_levels {
        integer cur_id
        varchar cur_name
        varchar cur_desc
        varchar cur_curator
    }
```

##### Publications
Genesets can be associated with publications. The publication table is contained in the
`production` schema. The publication table contains the following columns:

```mermaid
erDiagram
    geneset ||--o{  publication : associatedWith
    publication {
        integer pub_id
        varchar pub_authors
        varchar pub_title
        varchar pub_abstract
        varchar pub_journal
        varchar pub_volume
        varchar pub_pages
        varchar pub_month
        varchar pub_year
        varchar pub_pubmed
    }
```

##### Projects
Genesets can be added to projects. Project membership is modeled using an associative
(intermediate) table named the `project2geneset` table. The project and project2geneset
tables are contained in the `production` schema. The tables contain the following 
columns:
```mermaid
erDiagram
    geneset }o--|| project2geneset: containedIn
    project }o--|| project2geneset: contains
    project {
        integer pj_id
        integer usr_id
        varchar pj_name
        varchar pj_groups
        varchar pj_sessionid
        date pj_created
        text pj_notes
        char pj_star
    }
    project2geneset {
        integer pj_id
        bigint gs_id
        date modified_on
    }
```


### User Table
The user table is used to store user information, and is used to associate users with
other Geneweaver entities.
```mermaid
erDiagram
    geneset ||--o{  usr : createdBy
    usr }o--|| notifications: canHave 
    usr }o--|| usr2grp: memberOf
    grp }o--|| usr2grp: hasMember
    usr {
        integer usr_id
        varchar usr_first_name
        varchar usr_last_name
        varchar usr_email
        varchar usr_password
        varchar usr_prefs
        integer usr_admin
        timestamp usr_last_seen
        date usr_created
        text ip_addr
        varchar apikey
        boolean is_guest
        varchar usr_sso_id
    }
    notifications {
        integer notification_id
        text message
        integer usr_id
        timestamp time_sent
        boolean read
        varchar subject
        boolean dismissed
    }
    grp {
        integer grp_id
        varchar grp_name
        boolean grp_private
        date grp_created
    }
    usr2grp {
        integer usr_id
        integer grp_id
        integer u2g_privileges
        integer u2g_status
        varchar u2g_comment
        date u2g_created
    }
```

### Full Relational Diagram

!!! danger "Work In Progress"
    [//]: # (TODO)
    This page is currently under construction, and not **all** tables in the data model
    are currently listed on this page. This diagram **only** contains tables that have
    been defined in the page, and **does not** represent the full data model.

```mermaid
erDiagram
    geneset }o--|| geneset_value : hasA
    gene }o--|| geneset_value : hasA
    geneset ||--o{  usr : ownedBy
    geneset ||--o{  file : createdFrom
    geneset ||--o{  publication : associatedWith
    geneset ||--o{  curation_levels: hasA
    geneset ||--o{ species: hasA
    geneset }o--|| project2geneset: containedIn
    project }o--|| project2geneset: contains
    usr }o--|| notifications: canHave 
    usr }o--|| usr2grp: memberOf
    grp }o--|| usr2grp: hasMember
    geneset {
        bigint gs_id
        integer usr_id
        bigint file_id
        varchar gs_name
        varchar gs_abbreviation
        integer pub_id
        integer res_id
        integer cur_id
        varchar gs_description
        integer sp_id
        integer gs_count
        integer gs_threshold_type
        varchar gs_threshold
        varchar gs_groups
        varchar gs_attribution_old
        varchar gs_uri
        integer gs_gene_id_type
        date gs_created
        varchar admin_flag
        timestamp gs_updated
        varchar gs_status
        varchar gsv_qual
        integer gs_attribution
        boolean gs_is_edgelist
    }
    geneset_value {
        bigint gs_id
        bigint ode_gene_id
        numeric gsv_value
        bigint gsv_hits
        character_varying[] gsv_source_list
        numeric[] gsv_values_list
        boolean gsv_in_threshold
        date gsv_date
    }
    gene {
        bigint ode_gene_id
        varchar ode_ref_id
        integer gdb_id
        integer sp_id
        boolean ode_pref
        date ode_date
        bigint[] old_ode_gene_ids
    }
    file {
        bigint file_id
        bigint file_size
        varchar file_uri
        text file_contents
        varchar file_comments
        date file_created
        text file_changes
    }
    publication {
        integer pub_id
        varchar pub_authors
        varchar pub_title
        varchar pub_abstract
        varchar pub_journal
        varchar pub_volume
        varchar pub_pages
        varchar pub_month
        varchar pub_year
        varchar pub_pubmed
    }
    usr {
        integer usr_id
        varchar usr_first_name
        varchar usr_last_name
        varchar usr_email
        varchar usr_password
        varchar usr_prefs
        integer usr_admin
        timestamp usr_last_seen
        date usr_created
        text ip_addr
        varchar apikey
        boolean is_guest
        varchar usr_sso_id
    }
    notifications {
        integer notification_id
        text message
        integer usr_id
        timestamp time_sent
        boolean read
        varchar subject
        boolean dismissed
    }
    curation_levels {
        integer cur_id
        varchar cur_name
        varchar cur_desc
        varchar cur_curator
    }
    species {
        integer sp_id
        varchar sp_name
        integer sp_taxid
        integer sp_ref_gdb_id
        date sp_date
        varchar sp_biomart_info
        text sp_source_data
    }
    project {
        integer pj_id
        integer usr_id
        varchar pj_name
        varchar pj_groups
        varchar pj_sessionid
        date pj_created
        text pj_notes
        char pj_star
    }
    project2geneset {
        integer pj_id
        bigint gs_id
        date modified_on
    }
    grp {
        integer grp_id
        varchar grp_name
        boolean grp_private
        date grp_created
    }
    usr2grp {
        integer usr_id
        integer grp_id
        integer u2g_privileges
        integer u2g_status
        varchar u2g_comment
        date u2g_created
    }
```
