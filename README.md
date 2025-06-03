# internship

Summary of Cleaning: Amazon Dataset
Clean the Column Names

df.columns = (
    df.columns
    .str.strip()                            # Remove leading/trailing spaces
    .str.lower()                            # Convert to lowercase
    .str.replace(' ', '_')                  # Replace spaces with underscores
    .str.replace(r'[^\w_]', '', regex=True) # Remove non-alphanumeric characters except underscores
)

    Renamed all columns to lowercase and snake_case.

    Removed â‚¹ and commas from price columns; converted to float.

    Converted discount_percentage and rating_count to numeric.

    Removed duplicate records.
 Check for Nulls
# Count missing values in each column
df.isnull().sum()


# Fill missing values in a column with 'Unknown'
df['user_name'] = df['user_name'].fillna('Unknown')


    Standardized text in category and review_title.

# Fill missing values in a column with 'Unknown'
df['user_name'] = df['user_name'].fillna('Unknown')
    Replaced pipe symbols (|) in product descriptions with full stops.

    Handled missing values using .dropna() where critical, .fillna() otherwise.
# Drop rows with missing values in critical columns
df = df.dropna(subset=['product_id', 'discounted_price', 'actual_price'])

# Drop rows where rating_count is missing
df = df.dropna(subset=['rating_count'])

    Exported clean CSV for analysis.
