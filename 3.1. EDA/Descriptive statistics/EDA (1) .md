import pandas as pd

# Đọc bộ dữ liệu HR từ file Excel vào DataFrame
sheet_name = 'HumanResources EmployeeDepartme' ##thay lần lượt các sheet 
hr_data = pd.read_excel('AdventureWorks2019_HR.xlsx', sheet_name=sheet_name)


# Kiểm tra giá trị bị thiếu/rỗng
missing_values = hr_data.isnull().sum()
print("Dữ liệu bị thiếu/rỗng:")
print(missing_values)

# Kiểm tra dòng dữ liệu bị trùng lặp
duplicate_rows = hr_data[hr_data.duplicated()]
num_duplicate_rows = len(duplicate_rows)
print("\nSố dòng dữ liệu bị trùng lặp:", num_duplicate_rows)

# Chọn các cột chính để phân tích
columns_to_analyze = ['EndDate'] ## thay lần lượt tên cột chính cần phân tích 
selected_data = hr_data[columns_to_analyze]

# Số dòng dữ liệu của các cột được chọn
num_rows_selected_data = len(selected_data)
print("\nSố dòng dữ liệu của các cột được chọn:", num_rows_selected_data)

# Bảng tứ phân vị (Descriptive statistics) của bộ dữ liệu đầu vào
columns_to_analyze = ['EndDate'] ## thay lần lượt dựa theo cột chính cần phân tích 

# Lấy các giá trị của cột dữ liệu đã chọn
selected_column_data = hr_data[columns_to_analyze]

# Tính toán bảng tứ phân vị cho cột dữ liệu đã chọn
descriptive_stats_column = selected_column_data.describe()

# In ra bảng tứ phân vị
print("\nBảng tứ phân vị của cột dữ liệu '{}'".format(columns_to_analyze))
print(descriptive_stats_column)
# descriptive_stats = hr_data.describe()
# print("\nBảng tứ phân vị của bộ dữ liệu đầu vào:")
# print(descriptive_stats)