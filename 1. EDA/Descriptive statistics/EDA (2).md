import pandas as pd

# Đọc bộ dữ liệu HR từ file Excel vào DataFrame
sheet_name = 'HumanResources Shift' ## thay lần lượt tên các sheet 
hr_data = pd.read_excel('AdventureWorks2019_HR.xlsx', sheet_name=sheet_name)

# Chọn các cột bạn muốn phân tích
columns_to_analyze = ['ShiftID', 'Name', 'StartTime',  'EndTime'] ## thay lần lượt các cột cần phân tích 
# Tạo DataFrame để lưu kết quả EDA
eda_results = pd.DataFrame(columns=['Column', 'Missing Values', 'Duplicate Rows'])

# Kiểm tra giá trị bị thiếu/rỗng cho từng cột
for column in columns_to_analyze:
    missing_values = hr_data[column].isnull().sum()
    eda_results.loc[len(eda_results)] = [column, missing_values, 0]

# Kiểm tra dòng dữ liệu bị trùng lặp
num_duplicate_rows = len(hr_data[hr_data.duplicated()])
eda_results.loc[len(eda_results)] = ['Duplicate Rows', 0, num_duplicate_rows]

# Số dòng dữ liệu của các cột được chọn
num_rows_selected_data = len(hr_data)
eda_results.loc[len(eda_results)] = ['Total Rows', 0, num_rows_selected_data]

# In bảng kết quả EDA
print("\nKết quả EDA của bộ dữ liệu 'HumanResources Employee':")
print(eda_results)
