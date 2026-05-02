---
title: "Event 1"
date: 2026-03-21
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Bài thu hoạch “AWS First Cloud AI Journey Community Day 2026”

### Mục Đích Của Sự Kiện

- Kết nối với các chuyên gia Cloud và lãnh đạo công nghệ
- Khám phá những ứng dụng mới của **Cloud & Generative AI**
- Trải nghiệm các **demo thực tế** với tình huống doanh nghiệp
- Mở rộng cơ hội **networking** trong hệ sinh thái công nghệ

### Danh Sách Diễn Giả

- **Uyen** - Employer Branding, GoTymeX
- **Phuc (Jason) Dang** - Cloud Solution Architect, Platform Engineering Team, GoTymeX
- **Hai Bui** - Platform Engineering Manager, Platform Engineering Team, GoTymeX
- **Hieu Nguyen** - AI Engineer, AWS
- **Phong Nguyen** - Senior Software Engineer, AWS
- **Phat Pham** - Software Engineer, Katalon
- **Nguyen Hoang Viet Phap** - Cloud Engineer, VPBank

### Nội Dung Nổi Bật

#### Giới thiệu về GoTyme

- Tập đoàn ngân hàng số mở rộng tại các thị trường mới nổi
- Thị trường hiện tại: Nam Phi, Philippines
- Thị trường phát triển: Indonesia, Hồng Kông
- Mô hình hỗ trợ doanh nghiệp vừa và nhỏ giảm chi phí kinh doanh
- Trụ sở chính tại Singapore
- 70% nhân sự kỹ thuật đến từ Việt Nam đang làm việc cho GoTyme
- Đến 2025, nằm trong Top 100 công ty có ảnh hưởng
- GoTymeX: Trung tâm công nghệ và phát triển sản phẩm của Tyme Group tại Việt Nam
- Kiosk (Nam Phi, Philippines): Rút ngắn thời gian định danh và phát hành thẻ
- Giải pháp công nghệ GoTymeX: Tăng sức cạnh tranh cho công ty
- Nhân viên được hỗ trợ bằng nhiều công cụ hiện đại
- Có các chương trình phát triển tài năng trẻ
- Mỗi thực tập sinh có một mentor riêng
- Thời gian thực tập: 3–6 tháng

#### Giới thiệu về Platform Engineering tại GoTymeX

- Đóng gói toàn bộ kiến thức, dịch vụ, kết nối và xử lý dữ liệu để tái sử dụng và bán cho khách hàng
- Sản phẩm giúp nhà phát triển có thể tự triển khai mà không phụ thuộc nhiều vào đội vận hành
- Khác biệt với Cloud Engineering: Không cần hiểu rõ dịch vụ Cloud đã dùng
- Mục tiêu: Xây dựng nền tảng đáng tin cậy, triển khai nhanh, dễ mở rộng và thân thiện với nhà phát triển

#### GenAIOps Essential DevOps for Generative Application - Sự tiến hóa của kiến trúc AWS

- Chuyển đổi từ **hệ thống nguyên khối (monolithic)** sang **microservices** vào năm 2012
- Microservices giải quyết thách thức vận hành nhưng mang lại lớp phức tạp mới

#### GenAIOps - Quy trình Phân phối liên tục

Plan → Code → Build → Test → Release → Deploy → Operate → Monitor → Plan (lặp lại)

#### GenAIOps - Năng lực cốt lõi của DevOps

- **Tích hợp liên tục (CI)**
- **Phân phối liên tục (CD)**
- **Tự động hóa triển khai** với Infrastructure as Code (IaC)
- **Giám sát & Quan sát** với logging và tracing
- **Văn hóa hợp tác** giữa các nhóm

#### GenAIOps - Tự động hóa Workflow phát triển

- DevOps giới thiệu **tự động hóa** và **khả năng quan sát**
- Giúp vận hành hệ thống microservices ở quy mô lớn

#### GenAIOps - Độ phức tạp từ AI tạo sinh

- Ứng dụng AI tạo thêm **lớp phức tạp mới**
- Xuất hiện **GenAIOps Pipeline** để quản lý

#### GenAIOps - Năng lực cốt lõi của Agent

- Agent được thiết kế để **triển khai ở quy mô lớn**
- Giới thiệu **Amazon Bedrock AgentCore**

#### GenAIOps - Công cụ quan sát

- **Langfuse** cho tracing và monitoring
- **OpenTelemetry 101** cho chuẩn hóa observability
- **Langfuse trên AWS**

#### GenAIOps - Phần trình diễn

- Demo thực tế về GenAIOps

#### Shipping Code trong Kỷ nguyên Agentic - Kịch bản

- **Quy trình cũ**: Một người, một tác vụ, thực hiện tuần tự.
- **Quy trình mới với AI**: Nhiều agent chạy song song, Git worktree giúp tránh xung đột.
- **Anthropic Agent Steams**: Các agent chia sẻ ngữ cảnh, phối hợp để hoàn thành nhiệm vụ.
- **Vai trò mới của developer**: Từ coder sang supervisor, quản lý và điều phối agent.

#### Shipping Code - Công cụ

- Git worktree để cô lập môi trường
- Agent supervisor để điều phối
- Toolchain tùy chỉnh cho multi-repo

#### Shipping Code - Phân tích sâu
- Hạn chế single-agent: ngữ cảnh nhỏ, tuần tự, dễ tắc nghẽn
- Lợi ích multi-agent: sửa bug, phát triển tính năng, commit tự động song song

#### Shipping Code - Demo
- Tạo worktree → gán agent → commit độc lập → supervisor merge

#### Shipping Code - Sổ tay năng suất
- Prompt engineering
- Context engineering
- Harnessing engineering
- Học hỏi liên tục

#### Production-Grade Multimodal GenAI on AWS

- **Quy trình AI cũ**: Tìm kiếm từ khóa, dashboard rời rạc, dữ liệu phân mảnh.
- **Ngăn xếp AI mới**: Embedding đa phương tiện, không gian ngữ nghĩa thống nhất, agent tự động.

#### Production-Grade - Tìm kiếm đa phương tiện với Nova Embeddings

- Embedding thống nhất cho văn bản, hình ảnh, video, âm thanh, tài liệu.
- Khả năng truy xuất chéo phương tiện với độ chính xác cao, hỗ trợ đa ngôn ngữ.

#### Production-Grade - GraphRAG cho tri thức doanh nghiệp

- Bộ công cụ GraphRAG kết hợp cơ sở dữ liệu đồ thị với RAG.
- Tích hợp với LangChain, FAISS, OpenSearch cho tìm kiếm doanh nghiệp.

#### Production-Grade - Quy trình đa agent

- Thực thi song song, chia sẻ ngữ cảnh, cộng tác tự động.
- Xây dựng agent hội thoại serverless với Claude + LangGraph trên SageMaker.

#### Production-Grade - GenAI an toàn & quan sát được

- Guardrails đảm bảo tuân thủ và an toàn.
- Quan sát để giám sát quy trình và embedding.
- Triển khai serverless mở rộng dễ dàng.

### Những người đam mê công nghệ trong cộng đồng fcaj

- Vượt qua rào cản: Trong fcaj, những thành viên khiếm thính chứng minh rằng hạn chế thính giác không thể ngăn cản sự sáng tạo.
- Giúp đỡ bạn mới: Họ chủ động hỗ trợ những bạn khiếm thính mới gia nhập, hướng dẫn cách tiếp cận và hòa nhập với công nghệ.
- Truyền cảm hứng: Tinh thần kiên trì và niềm đam mê công nghệ của họ lan tỏa trong cộng đồng, khẳng định rằng đam mê vượt lên mọi giới hạn.

### Những Gì Học Được

#### Platform Engineering

- **Hệ thống tái sử dụng**: Đóng gói dịch vụ và dữ liệu để thương mại hóa.
- **Trao quyền cho nhà phát triển**: Tự triển khai mà không phụ thuộc nhiều vào vận hành.
- **Khả năng mở rộng & độ tin cậy**: Tập trung vào tốc độ, khả năng phục hồi và thiết kế thân thiện với lập trình viên.

#### GenAIOps & Tiến hóa DevOps

- **Chuyển sang microservices**: Giải quyết vấn đề hệ thống nguyên khối nhưng tăng độ phức tạp.
- **Tự động hóa CI/CD**: Hạ tầng dưới dạng mã, giám sát và khả năng quan sát.
- **Lớp AI sinh tạo**: Quản lý độ phức tạp mới thông qua pipeline GenAIOps.
- **AgentCore**: Triển khai quy mô lớn với Amazon Bedrock.
- **Công cụ quan sát**: Langfuse, OpenTelemetry cho truy vết và giám sát.

#### Viết mã trong kỷ nguyên Agentic

- **Từ lập trình viên thành người giám sát**: Nhà phát triển điều phối quy trình đa agent.
- **Thực thi song song**: Các agent xử lý nhiệm vụ đồng thời, giảm tắc nghẽn.
- **Công cụ hỗ trợ**: Git worktrees, agent supervisors, bộ công cụ tùy chỉnh.

#### GenAI đa phương tiện cấp độ sản xuất

- **Embedding thống nhất**: Văn bản, hình ảnh, video, âm thanh, tài liệu trong cùng không gian ngữ nghĩa.
- **GraphRAG**: Lý luận theo ngữ cảnh với tích hợp doanh nghiệp.
- **Quy trình đa agent**: Hợp tác tự động, triển khai serverless.
- **An toàn & khả năng quan sát**: Hàng rào bảo vệ và giám sát để tuân thủ.

#### Cảm hứng từ cộng đồng FCAJ

- **Phá bỏ rào cản**: Thành viên khiếm thính vẫn thành công trong công nghệ.
- **Hỗ trợ đồng đội**: Giúp người mới thích nghi.
- **Hình mẫu**: Kiên trì và đam mê truyền cảm hứng cho cộng đồng.

### Ứng Dụng Vào Công Việc

- **Tận dụng trung tâm nhân tài Việt Nam**: Khuyến khích hợp tác xuyên biên giới và đổi mới tại GoTymeX.
- **Áp dụng nguyên tắc kỹ thuật nền tảng**: Xây dựng hệ thống tái sử dụng, thân thiện với lập trình viên để giảm gánh nặng vận hành.
- **Tổ chức workshop event storming**: Áp dụng DDD để xác định ranh giới dịch vụ và cải thiện thiết kế microservices.
- **Triển khai pipeline GenAIOps**: Tự động hóa CI/CD với khả năng quan sát cho ứng dụng AI sinh tạo.
- **Thử nghiệm quy trình đa agent**: Sử dụng Git worktrees và agent supervisors để tăng năng suất.
- **Thí điểm giải pháp AI đa phương tiện**: Áp dụng Nova embeddings và GraphRAG cho quản lý tri thức doanh nghiệp.
- **Thúc đẩy văn hóa hòa nhập**: Hỗ trợ nhân tài đa dạng, lấy cảm hứng từ cách tiếp cận cộng đồng của FCAJ.

### Trải nghiệm trong event

Tham dự **AWS First Cloud AI Journey Community Day 2026** là một trải nghiệm đầy cảm hứng và giá trị, mang lại cái nhìn sâu sắc về tương lai của Cloud và AI. Những điểm nổi bật bao gồm:

#### Học hỏi từ các diễn giả tiên phong

- Chuyên gia AWS và các nhà đổi mới công nghệ chia sẻ **best practices** về platform engineering và GenAIOps.
- Các case study thực tế minh họa cách **microservices, công cụ quan sát, và multi-agent workflows** đang thay đổi hệ thống doanh nghiệp.

#### Trải nghiệm kỹ thuật thực tế

- Tham gia các **demo trực tiếp** về pipeline Generative AI, thể hiện tự động hóa trong CI/CD và giám sát.
- Khám phá **multi-agent orchestration** với Git worktrees và agent supervisors, nâng cao năng suất.
- Trải nghiệm **giải pháp AI đa phương thức** với unified embeddings và GraphRAG cho quản lý tri thức doanh nghiệp.

#### Ứng dụng công cụ hiện đại

- Tìm hiểu cách **Amazon Bedrock** hỗ trợ triển khai agent quy mô lớn.
- Khám phá các framework giám sát như **Langfuse** và **OpenTelemetry** để đảm bảo tuân thủ và khả năng phục hồi.

#### Networking và cảm hứng cộng đồng

- Giao lưu với đồng nghiệp và chuyên gia, tăng cường hợp tác xuyên biên giới.
- Truyền cảm hứng từ những câu chuyện về **sự hòa nhập**, nơi tài năng đa dạng—bao gồm cả thành viên khiếm thính—vẫn tỏa sáng trong công nghệ.

#### Bài học rút ra

- Nguyên tắc platform engineering giúp giảm gánh nặng vận hành và trao quyền cho developer.
- GenAIOps pipelines là chìa khóa để quản lý sự phức tạp trong ứng dụng Generative AI.
- Multi-agent workflows và multimodal AI mở ra khả năng mở rộng, phục hồi và đổi mới ở cấp độ mới.

#### Một số hình ảnh khi tham gia sự kiện

*Thêm các hình ảnh của các bạn tại đây*

> Tổng thể, sự kiện không chỉ cung cấp kiến thức kỹ thuật mà còn giúp tôi thay đổi cách tư duy về thiết kế ứng dụng, hiện đại hóa hệ thống và phối hợp hiệu quả hơn giữa các team.