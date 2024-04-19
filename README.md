# Preprocessing-Data
import pandas as pd
import numpy as np

class DataPrepKit:
    
    def read_data(file_path, file_format):
       
        if file_format == 'csv':
            return pd.read_csv(file_path)
        elif file_format == 'excel':
            return pd.read_excel(file_path)
        elif file_format == 'json':
            return pd.read_json(file_path)
        else:
            raise ValueError(f"Unsupported file format: {file_format}")

    
    def data_summary(df):
       
        return {
            'mean': df.mean(),
            'most_frequent': df.mode().iloc[0]
        }

    def handle_missing_values(df, strategy='remove'):
       
        if strategy == 'remove':
            return df.dropna()
        elif strategy == 'impute':
            return df.fillna(df.mean())
        else:
            raise ValueError(f"Unsupported strategy: {strategy}")

   
    def encode_categorical_data(df):
       
        return pd.get_dummies(df)

    
    def deploy_package():
       
        # Implement the PyPI deployment process here
        print("Deploying DataPrepKit package on PyPI...")


if __name__ == "__main__":
    # Reading data
    df = DataPrepKit.read_data("data.csv", "csv")
    print("Original Data:")
    print(df)
    
    
    summary = DataPrepKit.data_summary(df)
    print("\nData Summary:")
    print(summary)
    
    
    df_cleaned = DataPrepKit.handle_missing_values(df, strategy='impute')
    print("\nData after handling missing values:")
    print(df_cleaned)
    
    
    df_encoded = DataPrepKit.encode_categorical_data(df)
    print("\nData after encoding categorical data:")
    print(df_encoded)
    
    
    DataPrepKit.deploy_package()
