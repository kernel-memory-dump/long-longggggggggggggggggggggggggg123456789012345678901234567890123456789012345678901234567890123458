# long-longggggggggggggggggggggggggg123456789012345678901234567890123456789012345678901234567890123458
longggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggg123 gggggggggggggggggggggggggggggggggggggggggggg


Here is a simple flow chart:

```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
 ```   

```mermaid
sequenceDiagram
    participant Users as Users
    participant FTP as FTP Server
    participant S3 as S3 Bucket
    participant App as Application
    participant EC2 as EC2 Instances
    
    Users->>+FTP: Upload files
    FTP->>+S3: Run sync script, push files to S3 (excluding app folders)
    App->>+S3: Upload via pre-signed URL (AdminPanel)
    EC2->>+S3: Periodically pull data from S3
    S3-->>FTP: Ignore app-controlled folders (Banners,Tabs)
    S3-->>EC2: Provide all available data

    FTP-->>Users: Sync complete, files available via assets.main-domain.com
    EC2-->>App: Process files pulled from S3
```
