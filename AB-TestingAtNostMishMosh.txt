# importing customer data
import noshmishmosh
# import numpy
import numpy as np

# Record of all visitors
all_visitors = noshmishmosh.customer_visits


# how many visitors wnd up buying 
paying_visitors = noshmishmosh.purchasing_customers

# Calculating the lengths of the two lists'
total_visitor_count = len(all_visitors)
paying_visitor_count = len(paying_visitors)

# Baseline rate
baseline_percent = (paying_visitor_count/total_visitor_count)*100
print('Baseline Percent is: ', baseline_percent)

# List of money spent by each customer in a typical week
payment_history = noshmishmosh.money_spent
# Average payment per customer
average_payment = np.mean(payment_history)

# Number of payments to clear $1240
new_customers_needed = np.ceil(1240/average_payment)

# Additional percent of visitors who must make a purchase in order to make this change worthwhile
percent_point_increase = (new_customers_needed/total_visitor_count)* 100
print('Percent point increase is: ', percent_point_increase)

# Minimum Detectable Effect
mde = (percent_point_increase/baseline_percent)*100
print('Minimum Detectable Effect is: ', mde)


# Significance threshold value 
significance_threshold = 0.1

# Sample size
ab_sample_size = 500
