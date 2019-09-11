：# MFRM
====
Environment:<br>
------
1. The project is implemented in C++.<br>
2. Microsoft Visual Studio Express 2015 for Windows Desktop IDE environment.<br>
3. Boost libraries need to be introduced,whose version is 1.68.0. compile x64.<br>

Supplement:<br> 
------	
	targetver.h:show Windows platform adaption<br>
	stdafx.h:include common libraries<br>
	stdafx.cpp<br>
	typed_directed_graph.h:Base class and function for initializing graph and deploying facilities<br>
	typed_directed_graph.cpp:candidates and reference locations data<br>
	geo_defines.h:Geo data types<br>
	greedy_k.h:Base class and function for greedy_k LNB<br>
	gen_datasets.h:Generate CA related data Synthesize user reference location data,Generate candidate location data correspond    		facility data on the road network	                                                                                     
	calculate_vertical_point:given a point,calculate its vertical point on a straight line,which is represented by two points
	gen_cands:output generated candidates
	gen_edges:output generated edges based on raw edges dataset,where only distances are replaced with Euclidean distance between 		vertices
	gen_ref_locs:Reference location data generation with distance limitation
	integrate_pois:integrate raw pois dataset into the data we need,and output results to file
	load_raw_pois:load raw pois dataset, and pick pois on demand
	load_vertices_and_edges:load vertices and edges datasets;also construct an R*-tree to organize edges
	pick_pois:pick pois from integrated pois dataset,and output results to file
	convert_datasets.h:Generate CA related data:Synthesize user reference location data,Generate candidate location data correspond 	facility data on the road network
	gen_cands:output generated candidates	   
	gen_edges:output generated edges based on raw edges dataset,where only distances are replaced with Euclidean distance between 		vertices
	gen_ref_locs:output generated reference locations
	load_and_pick_pois: load and pick pois, also including integration facilities
	load_edges_and_geos:load edges and sub-segments (geos) datasets;also construct an R*-tree to organize sub
	real_datasets.h:integrate real BJ and CA datasets
	load_and_snap_reflocs_BJ:load and snap reference locations of BJ datases
	load_and_snap_reflocs_CA:load and snap reference locations of CA datases
	mindist.h:calculate for comparing with min-dist FR problems
	load_users_facs_cands:EN Load synthetic users, facilities,candidates data
	load_realusers_facs_cands:EN Load real users,facilities,candidates data
	md_load_users:min-dist:Load synthetic users data
	md_load_realusers:min-dist:Load real users data 
	md_load_facs:min-dist:Load facilities data
	md_load_cands:min-dist:Load candidates data
	md_load_en_results:EN:Load the resulting data of EN
	MINDIST:mid-dist:Calculate the resulting data
	MINDIST_FAST  
	solutions.h:Base class and function for EN,LNB,RID,RID-Q,greedy_k RID
	EN:EN algorithm
	LNB_top_visitor:top event visitor for LNB algorithm
	LNB_extend_visitor:extend event visitor for LNB algorithm
	LNB_construct_LNT:LNB algorithm:construct LNT and L2NT
	LNB_query:LNB algorithm:query optimal facility-replacement pair based on LNT & L2NT
	NNFC_visitor:top event visitor for calculate NNFC
	NSJ_visitor:top event visitor for NSJ algorithm
	NSJ_construct_NNFC:NSJ algorithm:construct NNFCs R-tree
	NSJ_query:NSJ algorithm:query optimal candidate based on NNFCs
	NNFC_RIC_visitor:top event visitor for calculate NNFC & RIC
	RID_construct_NNFC_and_RIC:RID algorithm:compute dr(f), i.e., \Delta(f), construct NNFC MBRs for reference locations and RIC 		MBRs for facilities                                                    		
	RID_query:RID algorithm:query optimal candidate based on RICs
	RID_new_querygreedy_k RID:query optimal candidate based on RICs
	RID_update_NNFC_and_RIC:greedy_k RID:compute dr(f), i.e., \Delta(f), construct NNFC MBRs for reference locations and RIC MBRs 		for facilities
	ir_utility.h                                              
	load_ranked_data:Load real or query data
	APatK:Calculate Precision (P),Recall (R) and Average Precision (AP)		
	MFRM.cpp:Main function           
	compare_EN_with_MinDist:Calculate for comparing with min-dist FR problems
	results_for_EN_MinDist                                                                        
	load_ranked_data:Calculate AP for two ranked sequences
	APatK:Implementation of all algorithoms (eg., EN,LNB,RID) in our paper             
	gen_datasets                                 
	convert_datasets                           
	real_datasets		            
Data:
-------
1. There are two datasets which are recorded by two folder:BJ_datasets and CA_datasets.<br>
2.The specific data file includes the following contents:<br>
	gen_edges:road network data.CA contains 21,693 bidirectional edges and 21,047 vertices.BJ consists of 433,391 				unidirectional edges and 171,504 vertices.<br>
	gen_cands_*:candidates location data.<br>
	gen_avg_reflocs_*:uniform distribution of reference locations data.
	gen_rand_reflocs_* :random distribution of reference locations data.
	real_reflocs:real users'reference locations data.The real users data of BJ is available from [33]in paper. There are 136,686 		sample points for each user on average. For CA, we use the discrete user check-in data[8] in paper.The average number of check-		ins for a user is about 125 after excluding users with less than 20 check-ins.The presence probabilities for reference 			locations of each user are skewed,where the differences between the maximum and minimum presence probabilities are 0.278 (CA) 		and 0.367 (BJ) on average.
	800_fac_xy:facility location data with coordinate
	800_fac:facility location data without coordinate
	The edges file format is "edge_id vs_id ve_id dist". 
	The facilities file format is "fac_id vs_id ve_id dist_vs_fac dist_fac_ve" or "fac_id vs_id ve_id dist_vs_fac dist_fac_ve lon 		lat".                          
	The candidates file format is "cand_id vs_id ve_id dist_vs_cand dist_cand_ve lon lat".
	The reference locations file format is "refloc_id vs_id ve_id dist_vs_refloc dist_refloc_ve prob lon lat".
Usage:<br>
-------
1.The program must be run in the specified directory:D:\Experiment\MFRMT
2. parameter setting: <br>
	Implements of all algorithoms: ...\config_CA.txt ...\gen_config.txt ...\cov_config.txt real_config.txt<br>
	Calculate for comparing with min-dist FR problems:first step:-md ...\config_MD.txt second 						step:-mdr ...\config_MD.txt<br>
3.In the configuration file,1 means execute and 0 means not execute,it can be modified according to the experimental requirements.<br>
