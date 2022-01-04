# NVR-algorithm
A clustering algorithm that consider the size of each point

For more backgroud and theories please check the following link
https://ray08datascience.medium.com/rvn-algorithm-c0a7ebde7f61

The sample data was randomized and did not represent any accurate floor plan, please only use it for practicing 

## Main API

### RVN_parameter_tuning(df,r_expand=1,rank_of_radius=0,print_current_group=False)
•	All parameters are same as RVN_naive
•	K_threshold is 2 because we want to try all possible K
•	Return sum of square error (SSE), silhouette score ,and K_list (All possible k)


### RVN_naive(df,K_threshold,r_expand=1,rank_of_radius=0,print_current_group=False)
•	df : dataframe of the floor plan
•	K_threshold: algorithm will stop when k <= K_threshold
•	rank_of_radius: [0,1,2,3], 0 is the biggest radius
•	r_expand: expansion speed, a constant number.
•	Print_current_group: True if you want to see the iteration of k
•	return an array for clusters


### RVN_approximate(df,K_threshold,print_current_group=False)
•	All parameters are same as RVN_naive
•	No r_expand because we will cluster two closest groups together when there is no overlapping group
•	return an array for clusters

## Other API

### get_centroid(df)
•	Calculate the new centroids
•	df: a group of point from the dataframe of the floor plan 


### get_radius(upper_x,upper_y,lower_x,lower_y,x,y,eps=0,rank_of_radius=0)
•	calculate the radius of the group
•	upper_x : the maximum of upper bound x of all point in this group
•	upper_y:  the max of upper bound y of all point in this group 
•	lower_x:  the minimum of lower bound x of all point in this group 
•	lower_y: the minimum of lower bound y of all point in this group
•	x: the x of the centroid
•	x: the x of the centroid
•	eps=0: if there is no overlapping point, eps will turn into r_expand to increase the radius, otherwise is 0
•	rank_of_radius=0: pick the rank of radius. We will have four possible radius
[x- upper_x, x- lower_x, y- upper_y, y- lower_y], we sort them in descending order. 0 is the largest radius. User can pick [0,1,2,3]

### Calculate_SSE(df,newdf)
•	df: data frame of floor with clusters of each point
•	newdf: data frame of centroid and radius all clusters
•	return sum of square error
•	
### Calculate_silhouette_score(df,newdf)
•	df: data frame of floor with clusters of each point
•	newdf: data frame of centroid and radius all clusters
•	return silhouette score

### get_two_closest_groups(df)
•	df: data frame of floor with clusters of each point
•	find two closest groups
•	return cluster number of two groups and the distance between them



