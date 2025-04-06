#Code cell <l4v-WiJNLCPT>
# %% [code]

# %% [code]
import pandas as pd
import matplotlib.pyplot as plt

# Arrays from the table
average_mass = [1.678, 1.586, 1.658, 1.617, 1.590, 1.655, 1.582, 1.675, 1.526, 1.697]
ann_average_mass = [1.66, 1.58, 1.66, 1.62, 1.61, 1.60, 1.53, 1.66, 1.46, 1.64]
rf_average_mass = [1.65, 1.60, 1.65, 1.62,  1.60, 1.64, 1.58, 1.66, 1.55, 1.67]
ada_boost_average_mass = [1.667, 1.586, 1.662, 1.618,  1.604, 1.654, 1.582, 1.657, 1.526, 1.683]



# Creating DataFrame
data = {
    'Density': average_mass,
    'ANN Density**': ann_average_mass,
     'RF Density**': rf_average_mass,
    'ADA Boost Density**': ada_boost_average_mass
   
}
df_average_mass = pd.DataFrame(data)

# Plotting
plt.figure(figsize=(14, 7))
plt.plot(df_average_mass['Density'], label='Actual Index of Refraction', marker='o', linewidth=3, markersize=8, color='black')
plt.plot(df_average_mass['ANN Density**'], label='ANN Index of Refraction', marker='x', linestyle='--', color='red')
plt.plot(df_average_mass['RF Density**'], label='RF Index of Refraction', marker='s', linestyle='--' , color='blue')
plt.plot(df_average_mass['ADA Boost Density**'], label='ADA Boost Index of Refraction', marker='d', linestyle='--', color='orange')

# Adding annotations to highlight differences with adjusted positions
for i, (actual, ann, rf, ada) in enumerate(zip(df_average_mass['Density'], df_average_mass['ANN Density**'], df_average_mass['RF Density**'], df_average_mass['ADA Boost Density**'])):
    plt.annotate(f'{actual}', (i, actual), textcoords="offset points", xytext=(0,10), ha='center', fontsize=8, color='black')
    plt.annotate(f'{ann}', (i, ann), textcoords="offset points", xytext=(15,-10), ha='center', fontsize=8, color='blue')
    plt.annotate(f'{rf}', (i, rf), textcoords="offset points", xytext=(-15,-10), ha='center', fontsize=8, color='green')
    plt.annotate(f'{ada}', (i, ada), textcoords="offset points", xytext=(15,-20), ha='center', fontsize=8, color='red')

plt.xlabel('Sample Index')
plt.ylabel('Index of Refraction')
# plt.title('Comparison of Actual and Predicted Average Mass')
plt.legend()
plt.grid(True)
plt.ylim(1.4,2)  # Adjusting y-axis limits to focus on the range of values
plt.show()
