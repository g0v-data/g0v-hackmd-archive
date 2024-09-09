Leftpane.vue

<template>
  <div class="left-pane">
    <div class="top-section">
      <n-input v-model="searchQuery" placeholder="搜尋ID/姓名" style="width: calc(100% - 100px)" @focus="handleInputFocus">
        <template #suffix>
          <SvgIcon :icon="'MagnifyingGlass'" size="12px" :style="{ color: searchQuery ? '#000' : '#8B8B8B' }"
            style="cursor: pointer" />
        </template>
      </n-input>

      <n-button ghost type="primary" @click="handleAddContact" style="margin-left: 8px; background-color: #fff"
        :disabled="!userPermissionStore.permissions.chatroom_create">
        <SvgIcon :icon="'Plus'" size="14px" style="cursor: pointer; margin-right: 6px" />
        新增聯絡人
      </n-button>
    </div>
    <div class="contact-list">
      <n-list v-if="hasPermissionToView">
        <n-list-item v-for="contact in filteredContacts" :key="contact.id" @click="selectContact(contact)" :class="[
        'contactClass',
        { selected: selectedContact && selectedContact.id === contact.id },
      ]">
          <div class="contact-item" style="gap: 10px">
            <div class="contact-name">
              {{ contact.name }}
            </div>
            <div class="latest-message">
              {{ cleanMessage(contact.lastMessage) || "" }}
            </div>
            
            <n-badge color="#47aed7"v-if="contact.unread_count && contact.unread_count > 0" :value="contact.unread_count" class="unread-badge"></n-badge>

            <div class="message-info">
              <SvgIcon
                v-if="contact.isUserRead && contact.isAdminRead"
                :icon="'Checks'"
                size="16px"
                :class="{
                  'read-icon': true,
                  'read-icon-selected': selectedContact && selectedContact.id === contact.id
                }"
              />
              <SvgIcon
                v-else-if="contact.isAdminRead || contact.isUserRead"
                :icon="'Check'"
                size="12px"
                :class="{
                  'read-icon': true,
                  'read-icon-selected': selectedContact && selectedContact.id === contact.id
                }"
              />
              <span
                class="message-time"
                :class="{
                  'message-time-selected': selectedContact && selectedContact.id === contact.id
                }"
              >{{ formatTime(contact.lastMessageTime) }}</span>
            </div>
          </div>
        </n-list-item>
      </n-list>
    </div>
    <CustomModal v-model:show="showPermissionModal" :bodyStyle="modalBodyStyle">
      <div>
        <p>此會員未同意管理 / 需會員同意管理才可以使用此功能</p>
        <n-button @click="closePermissionModal">確定</n-button>
      </div>
    </CustomModal>
  </div>
</template>

<script lang="ts" setup>
import { ref, computed, defineEmits, defineProps } from "vue";
import { Contact } from "@/types/index";
import { useContactDrawerStore } from "@/stores/drawers/ContactDrawerStore";
import { useChatroomPermissionStore } from "@/stores/permissions/chatroomPermissionStore"; 
import CustomModal from "@/components/common/CustomModal.vue"; 
import { updateChatRecordRead } from "@/services/api";
import { useChatStore } from "@/stores/chatroom/chat";
const chatStore = useChatStore();


import { useChatroomStore } from '@/stores/chatroom/leftpane';
const chatroomStore = useChatroomStore();

const emit = defineEmits(["select-contact"]);
const contactDrawerStore = useContactDrawerStore();
const props = defineProps({
  contacts: {
    type: Array as () => Contact[],
    required: true,
  },
});

const userPermissionStore = useChatroomPermissionStore(); 
const hasPermissionToView = computed(() => userPermissionStore.permissions.chatroom_search_user);

const searchQuery = ref<string>("");
const selectedContact = ref<Contact | null>(null);
const showPermissionModal = ref(false); 
const modalBodyStyle = {
  maxWidth: "384px",
  textAlign: "center",
  padding: "0px 0px 18px 0px",
};
const modalManuallyClosed = ref(false); 

const filteredContacts = ref<Contact[]>([]);

const formatTime = (time: string) => {
  if (!time) return '';
  const date = new Date(time);
  return `${date.getHours()}:${date.getMinutes().toString().padStart(2, '0')}`;
};

const handleInputFocus = () => {
  if (!userPermissionStore.permissions.chatroom_list && !modalManuallyClosed.value) {
    showPermissionModal.value = true;
  }
};

const handleAddContact = () => {
  if (!userPermissionStore.permissions.chatroom_create && !modalManuallyClosed.value) {
    showPermissionModal.value = true;
    return;
  }
  contactDrawerStore.openDrawer("add");
};

const closePermissionModal = () => {
  showPermissionModal.value = false;
  modalManuallyClosed.value = true;
  setTimeout(() => {
    modalManuallyClosed.value = false;
  }, 1000);
};

const selectContact = async (contact: Contact) => {
  selectedContact.value = contact;
  emit("select-contact", contact);

  // 加載聊天歷史
  await chatStore.loadChatHistory(contact.id); // 確保聊天歷史先加載完成

  // 過濾符合條件的未讀消息
  const unreadMessages = chatStore.chatHistory
    .filter(message => message.is_admin_read === false && message.is_user_speak === true)
    .map(message => message.chat_record_id); // 獲取未讀消息的 chat_record_id

  // 如果有未讀消息，打 PUT API 更新狀態
  if (unreadMessages.length > 0) {
    try {
      await updateChatRecordRead(unreadMessages); // 更新消息狀態為已讀

      // 更新本地消息狀態為已讀
      unreadMessages.forEach(id => {
        const message = chatStore.chatHistory.find(m => m.chat_record_id === id);
        if (message) {
          message.is_user_read = true;
        }
      });

    } catch (error) {
      console.error("Failed to update chat records:", error);
    }
  }
};

watch(
  () => chatroomStore.contacts,
  () => {

    filteredContacts.value = chatroomStore.contacts;
  },
  { immediate: true }
);



const cleanMessage = (message: any) => {
  if(!message) return '';
  return message.startsWith('%') && message.endsWith('%')
    ? message.slice(1 , -1) : message;
}

</script>

-

rightpane.vue
<template>
  <div class="right-pane-container">
    <div v-if="selectedContact" class="chat-header">
      <div class="contact-header-item" style="display: flex; align-items: center">
        <div class="contact-name" style="margin-right: 16px">
          {{ contactDetails.user_name }}
        </div>
        <div class="contact-details">
          年齡: {{ contactDetails.user_age }} / BMI: {{ contactDetails.user_bmi }} / 身高:
          {{ contactDetails.user_height }} / 體重: {{ contactDetails.user_weight }}<br />
          電話: {{ contactDetails.user_phone }} / Email: {{ contactDetails.user_mail }}
        </div>
      </div>
    </div>

    <div class="right-pane">
      <div v-if="!selectedContact" style="height: calc(100vh - 78px)"></div>
      <div class="chat-history" v-if="selectedContact">
        <div v-for="message in chatHistory" :key="message.chat_time" v-if="hasPermissionToView" class="message">
          <div :class="{ 'message-sent': message.is_admin_speak, 'message-received': !message.is_admin_speak }">


            <div v-if="isFileMessage(message.chat_content)">
              <n-space vertical>
                <div v-for="fileName in message.chat_content.split('\n').filter(name => name)" :key="fileName" class="fileStyle">
                  <n-space align="center" justify="start">
                    <SvgIcon icon="Paperclip" size="24px" />
                    <div>
          <a :href="getFileDownloadLink(fileName)" target="_blank" rel="noopener noreferrer" style="text-decoration:none">
            <div style="text-align: left">{{ extractFileName(fileName) }}</div>
            <div style="text-align:left;color:#C2C2C2;font-size:12px">123</div>
          </a>
        </div>
                  </n-space>
                </div>
              </n-space>
            </div>


            <div v-else>
              <!-- 普通消息 -->
              {{ message.chat_content }}
            </div>

            <div :class="['message-time', { 'message-time-right': message.is_admin_speak }]">
              <span>{{ formatTimestamp(message.chat_time) }}</span>
              <SvgIcon :icon="getIconType(message)" :size="getIconType(message) === 'Checks' ? '18px' : '10px'" :class="{
      'read-icon': getIconType(message) === 'Check',
      'read-icon-selected': isSelectedContact && getIconType(message) === 'Checks',
    }" />
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="chat-input">
      <div style="display: flex; width: 100%">
        <n-button quaternary type="primary" @click="handleFileUpload" :disabled="!selectedContact"
          style="margin-left: 0">
          <SvgIcon icon="Paperclip" size="18px" style="padding: 0" />
        </n-button>
        <n-input v-model:value="newMessage" placeholder="輸入訊息" style="flex-grow: 1; margin-right: 8px"
          :disabled="!selectedContact" @keyup.enter="sendMessage" />
        <n-button type="primary" @click="sendMessage" :disabled="!selectedContact" style="color: #fff">送出</n-button>
      </div>
    </div>
    <FileUploadModal :showFileModal="showFileModal" :files="files" @cancelFileUpload="cancelFileUpload"
      @confirmFileUpload="confirmFileUpload" />
  </div>
</template>

<script lang="ts" setup>
import { ref, nextTick, watch } from "vue";
import { Contact, Message } from "@/types/index";
import { useChatroomPermissionStore } from "@/stores/permissions/chatroomPermissionStore";
import { sendChatMessage, sendFileMessage } from "@/services/api";
import FileUploadModal from "../Chat/FileUploadModal.vue";
import { formatFileSize, formatTimestamp } from "@/utils/formatters";
import { useChatroomStore } from '@/stores/chatroom/leftpane';
import { useChatStore } from "@/stores/chatroom/chat";
const chatStore = useChatStore();
const files = ref<File[]>([]);
const showFileModal = ref(false)
const props = defineProps({
  selectedContact: {
    type: Object as () => Contact | null,
    default: null,
  },
});
const chatroomStore = useChatroomStore();
const newMessage = ref("");
const chatHistory = computed(() => chatStore.chatHistory);
const contactDetails = ref({
  user_name: "",
  user_age: "",
  user_bmi: "",
  user_height: "",
  user_weight: "",
  user_phone: "",
  user_mail: ""
});

const userPermissionStore = useChatroomPermissionStore();
const hasPermissionToView = computed(() => userPermissionStore.permissions.chatroom_history);
const isSelectedContact = computed(() => props.selectedContact !== null);

watch(
  () => props.selectedContact,
  async (newVal) => {
    if (newVal) {
      // 清空當前聊天記錄
      chatStore.chatHistory = [];
      
      // 聯絡人詳細資訊和聊天歷史
      contactDetails.value = await chatStore.loadContactDetails(newVal.id) || contactDetails.value;
      const history = await chatStore.loadChatHistory(newVal.id);
      chatStore.setChatHistory(history);

      // 滾動到最新消息
      nextTick(() => {
        const chatHistoryElement = document.querySelector(".chat-history");
        if (chatHistoryElement) {
          chatHistoryElement.scrollTop = chatHistoryElement.scrollHeight;
        }
      });

      // 更新聯絡人列表
      await chatroomStore.loadChatList();  // 確保更新左側列表
    }
  }
);


const getIconType = (message: any) => {
  if (message.is_user_read && message.is_admin_read) {
    return 'Checks'; // 確保返回字串
  } else if (message.is_user_read || message.is_admin_read) {
    return 'Check'; // 確保返回字串
  } else {
    return ''; // 返回空字串以避免錯誤
  }
};


const handleFileUpload = () => {
  const input = document.createElement("input");
  input.type = "file";
  input.multiple = true; // 允許選擇多個檔案
  input.onchange = (event: Event) => {
    const selectedFiles = Array.from((event.target as HTMLInputElement).files || []);
    files.value = selectedFiles; // 儲存選中的檔案
    showFileModal.value = true;
  };
  input.click();
};

const cancelFileUpload = () => {
  files.value = [];
  showFileModal.value = false;
};

const confirmFileUpload = async () => {
  if (!props.selectedContact || files.value.length === 0) return;

  // 構建 FormData 來處理檔案上傳
  const formData = new FormData();
  formData.append("user_id", props.selectedContact.id);
  files.value.forEach((file) => {
    formData.append("files", file);
  });
  formData.append("is_admin_speak", "true");

  try {
    // 呼叫上傳檔案 API
    const response = await sendFileMessage(formData);
    if (response.data.error_code === 0) {
      const chatRecordId = response.data.chat_record_id;
      // 將每個檔案包裝成 `%filename%` 的格式
      const fileMessageContent = files.value.map(file =>
        `%${file.name}%`
      ).join('\n');

      chatHistory.value.push({
        contactId: props.selectedContact.id,
        chat_content: fileMessageContent,
        chat_time: new Date().toISOString(),
        is_user_speak: false,
        is_admin_speak: true,
        is_user_read: false,
        is_admin_read: true,
        chat_record_id: chatRecordId,
      });

      showFileModal.value = false;
      files.value = [];

      // 滾動到最新訊息
      nextTick(() => {
        const chatHistoryElement = document.querySelector(".chat-history");
        if (chatHistoryElement) {
          chatHistoryElement.scrollTop = chatHistoryElement.scrollHeight;
        }
      });

      await chatroomStore.loadChatList();
    } else {
      console.error("Failed to send file:", response.data.error_desc);
    }
  } catch (error) {
    console.error("Error sending file:", error);
  }
};

const sendMessage = async () => {
  if (!newMessage.value || !props.selectedContact) {
    return;
  }

  try {
    const response = await sendChatMessage(props.selectedContact.id, newMessage.value, true);
    const chatRecordId = response.data.chat_record_id;
    if (response.data.error_code === 0) {
      chatStore.addMessage({
        contactId: props.selectedContact.id,
        chat_content: newMessage.value,
        chat_time: new Date().toISOString(),
        is_user_speak: false,
        is_admin_speak: true,
        is_user_read: false,
        is_admin_read: true,
        chat_record_id: chatRecordId,
      });

      // 清空輸入框
      newMessage.value = "";

      // 滾動到最新的消息
      nextTick(() => {
        const chatHistoryElement = document.querySelector(".chat-history");
        if (chatHistoryElement) {
          chatHistoryElement.scrollTop = chatHistoryElement.scrollHeight;
        }
      });

      await chatroomStore.loadChatList();
    } else {
      console.error("Failed to send message:", response.data.error_desc);
    }
  } catch (error) {
    console.error("Error sending message:", error);
  }
};

const isFileMessage = (content: string | null | undefined) => {
  // 如果 content 是 undefined 或 null，返回 false
  if (!content) return false;
  return content.startsWith('%') && content.endsWith('%');
};


const extractFileName = (content: string) => {
  return content.slice(1, -1); // 去除前後的 % 符號來提取檔案名稱
};

const getFileDownloadLink = (fileName: string) => {
  const cleanFileName = extractFileName(fileName);
  return `/download?fileName=${encodeURIComponent(cleanFileName)}`;
};

</script>

--

chat.ts

import { defineStore } from 'pinia';
import { ref } from 'vue';
import { openDB } from 'idb';
import { Contact, Message } from '@/types/index';
import { fetchChatHistory, fetchChatUserInfo } from '@/services/api';

export const useChatStore = defineStore('chat', () => {
  const maxCacheSize = 10;
  const cacheOrder = ref<string[]>([]);
  const chatHistory = ref<Message[]>([]); // 用於存儲聊天歷史的響應式數據
  

  const addMessage = async (message: Message) => {
    chatHistory.value.push(message);  // 將新消息添加到聊天歷史
    const contactId = message.contactId;
    if (!contactId) {
      console.error("No contactId specified for message.");
      return;
    }
    // 更新 IndexedDB 中的數據
    const db = await dbPromise;
    const cachedHistory = await db.get('chatHistory', contactId);  // 確保 contactId 有效
    const updatedMessages = cachedHistory ? [...cachedHistory.messages, message] : [message];
    await db.put('chatHistory', { contactId, messages: updatedMessages });
  };
  const setChatHistory = (messages: Message[]) => {
    chatHistory.value = messages;
  };

  let dbPromise: Promise<any>;

  // 初始化 IndexedDB
  const initDB = async () => {
    dbPromise = openDB('chat-database', 1, {
      upgrade(db) {
        if (!db.objectStoreNames.contains('chatHistory')) {
          db.createObjectStore('chatHistory', { keyPath: 'contactId' });
        }
        if (!db.objectStoreNames.contains('contactDetails')) {
          db.createObjectStore('contactDetails', { keyPath: 'contactId' });
        }
      }
    });
  };

  // 更新緩存順序
  const updateCacheOrder = async (contactId: string) => {
    const index = cacheOrder.value.indexOf(contactId);
    if (index > -1) {
      cacheOrder.value.splice(index, 1);
    }
    cacheOrder.value.push(contactId);

    if (cacheOrder.value.length > maxCacheSize) {
      const oldestContactId = cacheOrder.value.shift();
      if (oldestContactId) {
        const db = await dbPromise;
        await db.delete('chatHistory', oldestContactId);
        await db.delete('contactDetails', oldestContactId);
      }
    }
  };

  // 加載聊天歷史
  const loadChatHistory = async (contactId: string) => {
    const db = await dbPromise;
    const cachedHistory = await db.get('chatHistory', contactId);
    
    // if (cachedHistory) {
    //   updateCacheOrder(contactId);
    //   return cachedHistory.messages;
    // }

    // 優先從 API 獲取最新的數據
    try {
    const response = await fetchChatHistory(contactId);
    if (response.data.error_code === 0 && Array.isArray(response.data.data)) {
      const messages = response.data.data.map((msg: any) => ({
        chat_content: msg.chat_content,
        chat_record_id : msg.chat_record_id,
        chat_time: msg.chat_time,
        is_user_speak: msg.is_user_speak,
        is_admin_speak: msg.is_admin_speak,
        is_user_read: msg.is_user_read,
        is_admin_read: msg.is_admin_read,
      }));
  
        // 存入 IndexedDB
        await db.put('chatHistory', { contactId, messages });
        updateCacheOrder(contactId);
        chatHistory.value = messages; // 更新響應式數據
        return messages;
      } else {
        console.warn("No chat history available for this contact.");
        return cachedHistory ? cachedHistory.messages : [];
      }
    } catch (error) {
      console.error("Error fetching chat history:", error);
      return cachedHistory ? cachedHistory.messages : [];
    }
  };

  // 新增 addMessageToHistory 方法來處理新消息的插入
  const addMessageToHistory = async (message: Message, contactId: string) => {
    const db = await dbPromise;
    
    // 將新消息添加到 chatHistory
    chatHistory.value.push(message);

    // 更新 IndexedDB 中的聊天歷史
    const cachedHistory = await db.get('chatHistory', contactId);
    const updatedMessages = cachedHistory ? [...cachedHistory.messages, message] : [message];
    await db.put('chatHistory', { contactId, messages: updatedMessages });
  };

  // 加載聯絡人詳細資訊
  const loadContactDetails = async (contactId: string) => {
    const db = await dbPromise;
    const cachedDetails = await db.get('contactDetails', contactId);
    if (cachedDetails) {
      updateCacheOrder(contactId);
      return cachedDetails.details;
    }

    try {
      const response = await fetchChatUserInfo(contactId);
      if (response.data.error_code === 0 && response.data.data) {
        const details = response.data.data;

        // 存入 IndexedDB
        await db.put('contactDetails', { contactId, details });
        updateCacheOrder(contactId);
        return details;
      } else {
        console.error('Failed to fetch contact details:', response.data.error_desc);
      }
    } catch (error) {
      console.error('Error fetching contact details:', error);
    }

    return null;
  };
  

  // 初始化 IndexedDB
  initDB();

  return {
    chatHistory,
    loadChatHistory,
    addMessageToHistory, // 暴露出來的更新方法
    loadContactDetails,
    setChatHistory,
    addMessage
  };
});


-

Chatroom.vue
<template>
  <div style="display: flex" class="chatContainer">
    <ContactList :contacts="chatroomStore.contacts" @select-contact="handleSelectContact" />
    <ChatPane :selectedContact="selectedContact" />
    <ContactDrawer @refreshContacts="loadChatList" />
  </div>
</template>

<script lang="ts" setup>
import { ref, onMounted } from "vue";
import ContactList from "@/components/Chat/LeftPane.vue";
import ChatPane from "@/components/Chat/RightPane.vue";
import ContactDrawer from "@/components/Drawer/ChatRoom/ContactDrawer.vue";
import { fetchChatList  } from "@/services/api";
import { Contact } from "@/types/index";
import { useFetchPermissions } from '@/hooks/useFetchPermissions';
import { useChatroomPermissionStore } from "@/stores/permissions/chatroomPermissionStore";
import { useChatroomStore } from '@/stores/chatroom/leftpane';

const contacts = ref<Contact[]>([]);
const selectedContact = ref<Contact | null>(null);
const isPermissionsLoaded = ref(false);

// 權限存儲
const permissionStore = useChatroomPermissionStore();
const chatroomStore = useChatroomStore();

const loadChatList = async () => {
  try {
    const response = await fetchChatList(null, 1, 10);
    if (response.data.error_code === 0) {
      contacts.value = response.data.data.map((chat: any) => ({
        id: chat.user_id,
        chatID: chat.chat_id,
        name: chat.user_name,
        lastMessage: chat.chat_content,
        lastMessageTime: chat.last_chat_time,
        isUserRead: chat.is_user_read,
        isAdminRead: chat.is_admin_read,
      }));
    } else {
      console.error("Failed to fetch chat list:", response.data.error_desc);
    }
  } catch (error) {
    console.error("Error fetching chat list:", error);
  }
};

const handleSelectContact = (contact: Contact) => {
  selectedContact.value = contact;
};

onMounted(async () => {
  try {
    await useFetchPermissions(permissionStore, "244629480973410299");
    isPermissionsLoaded.value = true;
    await chatroomStore.loadChatList();
  } catch (error) {
    console.error("Error fetching permissions:", error);
  }
});
</script>


好，但改這樣後，我希望點leftpane後，rightpane的歷史訊息是可以直接更新成已讀
或者是，我點leftpane的item後，右側可以刷新

